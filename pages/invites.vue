<template>
  <div >
    Yth. {{names[this.in]}}   
    <br /><br />
    Tanpa mengurangi rasa hormat, dengan segala kerendahan hati dan dengan
    ungkapan syukur atas karunia Tuhan, kami mengundang {{ names[this.in] }}
    untuk hadir di acara pernikahan kami:
    <br /><br />
    Berliana Savira Putri & Alan Raihan Maulana. 
    <br /><br />
    Undangan dapat diakses melalui:
    https://julythirteen.com/?honors={{ names[this.in].replace(/ /g, '+') }}
    <br /><br />
    Merupakan suatu kebahagiaan bagi kami apabila Saudara/Saudari dapat berkenan
    hadir untuk memberikan doa restu kepada kami. 
    <br /><br />
    Atas kehadiran dan doa restunya
    kami ucapkan terima kasih.
    <br />
    Regards, Berlin and Alan
    <br /><br />
  </div>
</template>

<script>
export default {
mounted() {
    
const params = new URLSearchParams(window.location.search);
this.in = params.get("in") || 0;
    },
  data() {
    return {
    in: 0,
      names: [
        "Novi dan Partner",
        "Opi dan Partner",
        "Faisal dan Partner",
        "Fahmi dan Partner",
        "Mala dan Partner",
        "Fina dan Partner",
        "Satrya dan Partner",
        "Salwa dan Partner",
        "Melisa dan Partner",
        "Elisa dan Partner",
        "Annisa Rima dan Partner",
        "Maista dan Partner",
        "Emil dan Partner",
        "Vickry dan Partner",
        "Asma dan Partner",
        "Fahmi dan Partner",
        "Alief dan Partner",
        "Pak Billy dan Partner",
        "Ali Wafa dan Partner",
        "Maista dan Partner",
        "Arif dan Partner",
        "Ino dan Partner",
        "Dimas dan Partner",
        "Faisal dan Partner",
        "Daffa dan Partner",
        "Amel dan Partner",
        "Khoer dan Partner",
        "Alfi dan Partner",
        "Dicky dan Partner",
        "Enrico dan Partner",
        "Daniel dan Partner",
      ],
    };
  },
};
</script>
<style lang="scss" scoped>
div {
    background-color: white;
    border: 1px solid rgba($color: #000000, $alpha: 0.25);
    margin: 20px;
    width: 800px;
    padding: 16px;
    border-radius: 12px; 
    box-shadow: 0 0 100vmax 100vmax rgba(0, 0, 0, 0.05);
}
</style>