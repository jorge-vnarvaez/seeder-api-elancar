<template>
  <div id="app">
    <button @click="poblarSolicitudesDeCotizacion">
      Poblar Solicitudes de Cotizacion
    </button>
    <button @click="poblarOrdenesDeCompra">
      Poblar Ordenes de Compra
    </button>
    <button @click="poblarCotizacionesCliente">
      Poblar Cotizaciones Cliente
    </button>
  </div>
</template>

<script>
import moment from "moment";
import axios from "axios";

export default {
  data() {
    return {
      metodos_de_pago: [
        "Efectivo",
        "Tarjeta de Credito",
        "Tarjeta de Debito",
        "Transferencia Bancaria",
        "Cheque",
      ],
      condiciones_de_venta: [30, 60, 90],
    };
  },
  methods: {
    async poblarSolicitudesDeCotizacion() {
      for (let i = 0; i < 10; i++) {
        const randomDate =
          new Date().getTime() + Math.floor(Math.random() * 10000000000);

        const randomMetodo = Math.random() * (this.metodos_de_pago.length - 1);
        const randomCondicion =
          Math.random() * (this.condiciones_de_venta.length - 1);

        const fecha_emision = moment(randomDate).format("YYYY-MM-DD");
        const hora_emision = moment(randomDate).format("HH:mm:ss");

        const metodo_de_pago = this.metodos_de_pago[Math.floor(randomMetodo)];
        const condicion_de_venta =
          this.condiciones_de_venta[Math.floor(randomCondicion)];

        await axios.post(
          `https://corev2.domhhv.cl/items/cotizaciones_proveedor`,
          {
            fecha_emision,
            hora_emision,
            "forma_de_pago": metodo_de_pago,
            "condiciones_de_venta": condicion_de_venta,
          }
        );
      }
    },
    async poblarOrdenesDeCompra() {
      for (let i = 0; i < 10; i++) {
        const randomDate =
          new Date().getTime() + Math.floor(Math.random() * 10000000000);

        const randomMetodo = Math.random() * (this.metodos_de_pago.length - 1);
        const randomCondicion =
          Math.random() * (this.condiciones_de_venta.length - 1);

        const fecha_emision = moment(randomDate).format("YYYY-MM-DD");
        const hora_emision = moment(randomDate).format("HH:mm:ss");

        const metodo_de_pago = this.metodos_de_pago[Math.floor(randomMetodo)];
        const condicion_de_venta =
          this.condiciones_de_venta[Math.floor(randomCondicion)];

        await axios.post(
          `https://corev2.domhhv.cl/items/ordenes_de_compra`,
          {
            fecha_emision,
            hora_emision,
            "forma_de_pago": metodo_de_pago,
            "condiciones_de_venta": condicion_de_venta,
          }
        );
      }
    },
    async poblarCotizacionesCliente() {
      for (let i = 0; i < 10; i++) {
        const randomDate =
          new Date().getTime() + Math.floor(Math.random() * 10000000000);

        const randomMetodo = Math.random() * (this.metodos_de_pago.length - 1);
        const randomCondicion =
          Math.random() * (this.condiciones_de_venta.length - 1);

        const fecha_emision = moment(randomDate).format("YYYY-MM-DD");
        const hora_emision = moment(randomDate).format("HH:mm:ss");

        const metodo_de_pago = this.metodos_de_pago[Math.floor(randomMetodo)];
        const condicion_de_venta =
          this.condiciones_de_venta[Math.floor(randomCondicion)];

        await axios.post(
          `https://corev2.domhhv.cl/items/cotizaciones_clientes`,
          {
            fecha_emision,
            hora_emision,
            "forma_de_pago": metodo_de_pago,
            "condiciones_de_venta": condicion_de_venta,
          }
        );
      }
    },
  },
  
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
