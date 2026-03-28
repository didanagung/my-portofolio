<template>
  <section class="h-full flex flex-col md:flex-row">
    <div class="md:flex-1/2 flex items-center justify-center">
      <h1 class="font-extrabold text-3xl md:text-6xl text-[#00a9be]">
        Contact me
      </h1>
    </div>
    <div class="md:flex-1/2 flex items-center justify-center flex-col gap-5">
      <h5 class="desc mx-auto w-10/12" >
          Hai, jika ada pertanyaan atau ada yang ingin di diskusikan? <br/> jangan sungkan untuk kontak saya ya 😊.
      </h5>
      <div class="flex flex-col gap-3 mx-auto w-10/12">
        <UInput size="xl" v-model="input.name" placeholder="Nama anda"/>
        <UInput size="xl" v-model="input.email" trailing-icon="i-lucide-at-sign" placeholder="Email anda" />
        <p v-if="emailNotValid" class="text-red-600">Format email salah.</p>
        <UTextarea size="xl" v-model="input.pesan" placeholder="Pesan anda..." />
        <p v-if="belumLengkap" class="text-red-600">Lengkapi form diatas.</p>
        <UButton :ui="{ base: 'justify-center text-center w-full' }" icon="i-lucide-rocket" size="md" color="primary" variant="solid" :loading="isLoading" @click="sendMessage">Kirim</UButton>
        <UAlert
          title="Terimakasi!"
          description="Pesan anda akan saya balas secepat mungkin di Email 😊"
          icon="i-lucide-terminal"
          v-if="pesanBerhasil"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
  const input = ref({
    dari: "Pesan dari Web Portofolio"
  })
  const isLoading = ref(false)
  const belumLengkap = ref(false)
  const emailNotValid = ref(false)
  const pesanBerhasil = ref(false)
  const emailTujuan = ref('xosive1319@muncloud.com')

  const sendMessage = async() => {
    if (!input.value.name || !input.value.email || !input.value.pesan) {
      belumLengkap.value = true
      return
    } else {
      belumLengkap.value = false
    }

    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
    if (!regex.test(input.value.email)) {
      emailNotValid.value = true
      return
    } else {
      emailNotValid.value = false
    }

    try {
      isLoading.value = true

      const res = await $fetch(`https://formsubmit.co/ajax/${emailTujuan.value}`, {
        method: 'POST',
        body: {
          name: input.value.name,
          email: input.value.email,
          message: input.value.pesan,
          _subject: input.value.dari,
          _template: 'table',
          _captcha: 'false',
        }
      })

      const toJson = JSON.parse(res)
      if (toJson.success == "true") {
        pesanBerhasil.value = true
        setTimeout(() => {
          pesanBerhasil.value = false
        }, 5000) // 2 detik
      }

      input.value = {
        dari: "Pesan dari Web Portofolio"
      }
    } catch (err) {
      console.error(err)
    } finally {
      isLoading.value = false
    }
  }
</script>

<style scoped>
  .desc {
    font-family: 'Inter', sans-serif;
  }
</style>
