<script>
  export let projects = [
    { url: "./first-article", projectName: "This site" },
    { url: "./first-article", projectName: "This site" },
    { url: "./first-article", projectName: "This site" },
    { url: "./first-article", projectName: "This site" },
  ];
  let lastHovered = 0;
</script>

<section id="projects">
  <h2>Здравей свят</h2>
  <hr />
  <div class="projects">
    {#each projects as project, id}
      <div class="project {lastHovered == id ? 'last-hovered' : ''}">
        <a
          href={project.url}
          on:mouseover={() => {
            lastHovered = id;
          }}
          on:focus
        >
          <h3>
            <span>
              {project.projectName}
            </span>
          </h3>
          <hr />
        </a>
      </div>
    {/each}
  </div>
</section>

<style lang="scss">
  @import "../styles/breaking_points.scss";
  @import "../styles/colors.scss";
  #projects {
    hr {
      border-top-color: black;
    }
    .project {
      a {
        display: block;
        width: 100%;
        text-decoration: none;
        color: $grey;
        display: flex;
        flex-direction: column;
        align-items: center;
        filter: blur(1px);
        & > * {
          transition: 0.9s;
        }
        h3 {
          font-family: "Cormorant SC", serif;
          padding: 1rem 0;
        }
        hr {
          border-top-color: $grey;
          justify-self: flex-end;
          margin: 0;
        }
      }
      &.last-hovered {
        a {
          filter: blur(0);
          h3 {
            color: $black;
          }
          hr {
            border-top-color: $black;
          }
        }
      }
    }
  }

  main.dark {
    #projects {
      hr {
        border-top-color: $white;
      }
      .project {
        a {
          filter: blur(1px);
          transition: 0.9s;
        }
        &.last-hovered {
          a {
            filter: blur(0);
          }
          h3 {
            color: $white;
          }
          hr {
            border-top-color: $white;
          }
        }
      }
    }
  }
</style>
