<template>
  <Layout>
    <div class="container">
    	<img src="../../static/logo.svg" class="center" />
      	<Hero />
      	<iframe src="https://www.google.com/maps/d/embed?mid=1QYGsiVQbqc1EShkHCZKout43QDP10q4F" width="980" height="720" class="map"></iframe>
	<img src="../../uploads/maps-black.svg" class="center" />
      	<!-- <ProjectsGrid :projects="$page.projects.edges" /> -->
	<div class="container">
	    <div class="legend">
	    	<div class="icon">
			<img src="../../uploads/maps-black.svg" class="icon" />
		</div>
	    	<div class="text">
			Left Side Menu
		</div>
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

.container {height: 100%; width:100%; font-size: 0;}
.legend, .legend, .legend, .legend, .legend, .legend, .legend {display: inline-block; *display: inline; zoom: 1; vertical-align: top; font-size: 0;}
.legend {width: 25%;}
.icon, .text {display: inline-block; *display: inline; zoom: 1; vertical-align: top; font-size: 12px;}
.icon {width: 10%;}
.text {width: 90%;}

</style>
