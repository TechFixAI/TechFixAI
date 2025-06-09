function enviarMensaje(event) {
  if (event.key === 'Enter') {
    const input = document.getElementById('inputMensaje');
    const mensaje = input.value.trim();
    if (mensaje === '') return;

    mostrarMensaje('usuario', mensaje);
    responderIA(mensaje);
    input.value = '';
  }
}

function mostrarMensaje(autor, texto) {
  const chatbox = document.getElementById('chatbox');
  const div = document.createElement('div');
  div.className = `mensaje ${autor}`;
  div.textContent = texto;
  chatbox.appendChild(div);
  chatbox.scrollTop = chatbox.scrollHeight;
}

function responderIA(mensaje) {
  let respuesta;

  if (mensaje.toLowerCase().includes("motor")) {
    respuesta = "¿Ya verificaste si la salida del PLC está activa?";
  } else if (mensaje.toLowerCase().includes("sensor")) {
    respuesta = "Podrías revisar si el sensor está correctamente alineado.";
  } else {
    respuesta = "Buena pregunta. Vamos a investigarlo juntos.";
  }

  setTimeout(() => {
    mostrarMensaje('ia', respuesta);
  }, 1000);
}

function accion(tipo) {
  if (tipo === 'start') {
    document.getElementById('motor').textContent = "⚙️ Motor [ENCENDIDO]";
    document.getElementById('luces').textContent = "💡 Luz Piloto [ENCENDIDA]";
    mostrarMensaje('ia', "El motor está en marcha. Observa si responde correctamente.");
  }
}
