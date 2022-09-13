<template>
    <h3>Υπολογισμός δόσης</h3>
    <p>Επιλέξτε την προκαταβολή και την διάρκεια που σας συμφέρει</p>
</template>

<style scoped>
h3 {
    margin: 0;
    padding: 0;
    position: absolute;
    top: 52px;
 font-family: 'Roboto', sans-serif;
 font-size: 20px;
     font-weight: 700;
    width: 100%;
    height: 26px;
    text-align: center;
    letter-spacing: 0px;
    color: #323232;
    opacity: 1;
}

p {
    margin: 0;
    padding: 0;
    font-family: 'Roboto', sans-serif;
    /* Layout Properties */
    position: absolute;
    top: 86px;
font-size: 13px;
    width: 100%;
    height: 18px;
    /* UI Properties */
    text-align: center;
    letter-spacing: 0px;
    color: #323232;
    opacity: 1;
}

@media screen and (max-width: 600px) {

  h3, p {
    
    width: 99vw;
    box-shadow: none;
    font-size: 120% ;
   margin: 0px;
  
  }
  


}
</style>