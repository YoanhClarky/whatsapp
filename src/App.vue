<template>
  <div class="flex justify-center items-center min-h-screen bg-whatsapp-green">
    <form
      @submit.prevent="submitForm"
      class="bg-white p-8 rounded-lg shadow-md w-full max-w-md"
    >
      <h2 class="text-2xl font-bold text-whatsapp-dark mb-6">Contactez-nous</h2>
      <div class="mb-4">
        <label for="name" class="block text-whatsapp-dark font-medium mb-2"
          >Nom:</label
        >
        <input
          type="text"
          v-model="name"
          id="name"
          required
          class="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-whatsapp-light"
        />
      </div>
      <div class="mb-4">
        <label for="email" class="block text-whatsapp-dark font-medium mb-2"
          >Email:</label
        >
        <input
          type="email"
          v-model="email"
          id="email"
          required
          class="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-whatsapp-light"
        />
      </div>
      <div class="mb-6">
        <label for="message" class="block text-whatsapp-dark font-medium mb-2"
          >Message:</label
        >
        <textarea
          v-model="message"
          id="message"
          required
          class="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-whatsapp-light"
        ></textarea>
      </div>
      <button
        type="submit"
        class="w-full bg-whatsapp-dark text-white py-2 rounded-md hover:bg-whatsapp-light transition-colors"
      >
        Envoyer via WhatsApp
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      message: "",
    };
  },
  methods: {
    submitForm() {
      const whatsappNumber = "+242044842352";
      const textMessage = `Nom: ${this.name}\nEmail: ${this.email}\nMessage: ${this.message}`;
      const url = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(
        textMessage
      )}`;
      window.open(url, "_blank");
    },
  },
};
</script>

<style scoped>
/* Couleurs WhatsApp */
.bg-whatsapp-green {
  background-color: #25d366;
}

.text-whatsapp-dark {
  color: #075e54;
}

.bg-whatsapp-dark {
  background-color: #075e54;
}

.bg-whatsapp-light {
  background-color: #128c7e;
}

/* Transition pour le bouton */
button {
  transition: background-color 0.3s ease;
}
</style>
