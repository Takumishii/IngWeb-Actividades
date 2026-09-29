<template>
  <div class="container">
    <div class="form-card">
      <h2>Contacto</h2>
      <p class="subtitle">Escríbenos para consultas sobre turismo y cultura en Chillán.</p>
      
      <form @submit.prevent class="contact-form">
        <div class="form-group">
          <label for="nombre">Nombre:</label>
          <input type="text" id="nombre" placeholder="Tu nombre" required />
        </div>

        <div class="form-group">
          <label for="email">Correo Electrónico:</label>
          <input type="email" id="email" placeholder="Tu correo" required />
        </div>

        <div class="form-group">
          <label for="mensaje">Mensaje:</label>
          <textarea id="mensaje" rows="4" placeholder="Escribe tu mensaje" required></textarea>
        </div>

        <button type="submit" class="btn-submit">Enviar Mensaje</button>
      </form>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  padding: 2rem 1rem;
}

.form-card {
  background: #ffffff;
  padding: 2.5rem;
  border-radius: 10px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  width: 100%;
  max-width: 500px;
}

h2 {
  color: #8B0000;
  margin-bottom: 0.5rem;
}

.subtitle {
  color: #666;
  font-size: 0.95rem;
  margin-bottom: 1.5rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}

label {
  font-weight: bold;
  color: #333;
  font-size: 0.9rem;
}

input, textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 1rem;
  box-sizing: border-box;
  transition: border-color 0.2s, box-shadow 0.2s;
}

input:focus, textarea:focus {
  outline: none;
  border-color: #8B0000;
  box-shadow: 0 0 0 3px rgba(139, 0, 0, 0.15);
}

textarea {
  resize: vertical;
}

.btn-submit {
  background-color: #8B0000;
  color: white;
  border: none;
  padding: 0.85rem;
  font-size: 1rem;
  font-weight: bold;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.2s;
  margin-top: 0.5rem;
}

.btn-submit:hover {
  background-color: #660000;
}
</style>