<template>
  <Layout>
    <div class="container">
    	<img src="../../static/logo.svg" class="center" />
      	<Hero />
      	<iframe src="https://www.google.com/maps/d/embed?mid=1QYGsiVQbqc1EShkHCZKout43QDP10q4F" width="980" height="720"></iframe>
      	<!-- <ProjectsGrid :projects="$page.projects.edges" /> -->
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

.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}

export default {
  components: {
    Hero,
    ProjectsGrid,
    LatestJournals
  }
}
</script>
