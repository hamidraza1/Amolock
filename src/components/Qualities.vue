<template>
    <div class="QualitiesWrapper">
        <div class="QualitiesInfo">
            <div class="QualitiesTitle">KREATIV</div>
            <div class="QualitiesDescrip">Zahlreiche Oberflächen & farbenb für unendliche Gestaltungsmöglich</div>
        </div>
        <div class="QualitiesInfo">
            <div class="QualitiesTitle">VIELSEITIG</div>
            <div class="QualitiesDescrip">Umfangreiches Sortiment für Wohnen & Objekt</div>
        </div>
        <div class="QualitiesInfo">
            <div class="QualitiesTitle">HOCHWERTIG</div>
            <div class="QualitiesDescrip">Gute Strapazierfähigkeit dank bester Materialzusammensetzung</div>
        </div>
        <div class="QualitiesInfo">
            <div class="QualitiesTitle">SELBSTLIEGEND</div>
            <div class="QualitiesDescrip">Lose verlegbar dank hochwertiger Rückenbeschichtung</div>
        </div>
    </div>
</template>


<script>
export default {
  name: 'Qualities',
}
</script>

<style>
.QualitiesWrapper{
    display:flex ;
    padding:35px 0;
    background-color:rgb(247,247,247) ;
}
.QualitiesInfo{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 25%;
}
.QualitiesTitle{
    font-size:16px;
    font-weight: 800;
}
.QualitiesDescrip{
    width:70%;
    font-size:14px;
    margin:0 auto;
    text-align: center;
}
</style>