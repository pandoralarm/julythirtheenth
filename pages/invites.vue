<template>
  <div ref="invitation">
    Yth. {{ guestName }}<br /><br />

    Tanpa mengurangi rasa hormat, dengan segala kerendahan hati dan dengan
    ungkapan syukur atas karunia Tuhan, kami mengundang {{ guestName }} untuk
    hadir di acara pernikahan kami:
    <br /><br />

    Berliana Savira Putri & Alan Raihan Maulana. <br /><br />

    Undangan dapat diakses melalui:
    https://julythirteen.com/?honors={{ guestName.replace(/ /g, '+') }}
    <br /><br />

    Merupakan suatu kebahagiaan bagi kami apabila Saudara/Saudari dapat
    berkenan hadir untuk memberikan doa restu kepada kami.
    <br /><br />

    Atas kehadiran dan doa restunya kami ucapkan terima kasih.
    <br />

    Regards, Berlin and Alan
    <br /><br />

    <button @click="copyText">Salin Undangan</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      guestName: "Tamu Undangan",
    };
  },
  mounted() {
    const params = new URLSearchParams(window.location.search);
    const name = params.get("name");
    if (name) {
      this.guestName = decodeURIComponent(name.replace(/\+/g, ' '));
    }
  },
  methods: {
    copyText() {
      const div = this.$refs.invitation;
      const range = document.createRange();
      range.selectNodeContents(div);

      const selection = window.getSelection();
      selection.removeAllRanges();
      selection.addRange(range);

      try {
        document.execCommand("copy");
        selection.removeAllRanges();
        alert("Undangan telah disalin ke clipboard.");
      } catch (err) {
        alert("Gagal menyalin undangan.");
      }
    },
  },
};
</script>

<style lang="scss" scoped>
div {
  background-color: white;
  border: 1px solid rgba(0, 0, 0, 0.25);
  margin: 20px;
  width: 800px;
  padding: 16px;
  border-radius: 12px;
  box-shadow: 0 0 100vmax 100vmax rgba(0, 0, 0, 0.05);
  font-family: sans-serif;

  button {
    margin-top: 12px;
    padding: 8px 16px;
    background-color: #333;
    color: #fff;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-weight: bold;

    &:hover {
      background-color: #555;
    }
  }
}
</style>
