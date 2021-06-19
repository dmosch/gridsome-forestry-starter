<template>
  <Layout>
    <div class="container">
    	<img src="../../static/logo.svg" class="center" />
      	<!-- <Hero /> -->
      	<iframe src="https://www.google.com/maps/d/embed?mid=1QYGsiVQbqc1EShkHCZKout43QDP10q4F" width="980" height="720" class="map"></iframe>
      	<!-- <ProjectsGrid :projects="$page.projects.edges" /> -->
	<div class="container">
	    <div class="legend">
	    	<div class="icon"> <img src="../../uploads/maps-blue.svg" /> </div>
	    	<div class="text"> Búnquers </div>
	    </div>
	    <div class="legend">
	    	<div class="icon"> <img src="../../uploads/maps-yellow.svg" /> </div>
	    	<div class="text"> Museos </div>
	    </div>
	    <div class="legend">
	    	<div class="icon"> <img src="../../uploads/maps-uboot.svg" /> </div>
	    	<div class="text"> U-Boot </div>
	    </div>
	    <div class="legend">
	    	<div class="icon"> <img src="../../uploads/maps-blockhaus.svg" /> </div>
	    	<div class="text"> Blockhaus </div>
	    </div>
	    <div class="legend">
	    	<div class="icon"> <img src="../../uploads/maps-black.svg" /> </div>
	    	<div class="text"> Cementerios </div>
	    </div>
	    <div class="legend">
	    	<div class="icon"> <img src="../../uploads/maps-memorial.svg" /> </div>
	    	<div class="text"> Memoriales </div>
	    </div>
	    <div class="legend_long">
	    	<div class="icon"> <img src="../../uploads/maps-green.svg" /> </div>
	    	<div class="text"> Campos de concentración </div>
	    </div>
	</div>
    </div>
    <LatestJournals :journals="$page.journals.edges" />
  </Layout>
</template>

<page-query>
query Posts {
	projects: allProjectPost {
    edges {
      node {
        id
        date (format: "YYYY")
        title
        categories
        thumbnail (quality: 90)
        path
      }
    }
  },
  journals: allJournalPost (perPage: 4) {
    edges {
      node {
        id
        path
        title
      }
    }
  }
}
</page-query>

<script>
import Hero from "@/components/Hero"
import ProjectsGrid from "@/components/ProjectsGrid"
import LatestJournals from "@/components/LatestJournals"

export default {
  components: {
    Hero,
    ProjectsGrid,
    LatestJournals
  }
}
</script>

<style scoped>
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 80%;
}

.map {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 100%;
}

.container {height: 100%; width:100%; margin-top: 20px; margin-bottom: 20px; font-size: 0;}
.legend, .legend, .legend, .legend, .legend, .legend, .legend_long {display: inline-block; *display: inline; zoom: 1; vertical-align: middle;  text-align: center; font-size: 0;}
.legend {width: 30%;}
.icon, .text {display: inline-block; *display: inline; zoom: 1; vertical-align: middle; font-size: 14px;}
.icon {width: 10%;}
.text {margin-left: 10px; margin-right: 15px;}

</style>
