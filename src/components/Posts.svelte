<script>
  // import "../styles/posts.css";
  export let posts = [
    {
      title: "Заглавие Едно",
      date: "Юли 2020",
      description: "Това ще бъде описанието на поста",
      link: "https://www.notion.so/Logs-f8524af8e64643c38330cc1a12b066da",
      tags: ["Svelte", "Data Science"],
    },
    {
      title: "Заглавие Две",
      date: "Юли 2020",
      link: "./first-article",
      description:
        "Това ще бъде описанието на поста. Тука още мъничко текст да видя, как ще изглежда",
      tags: ["SolidJS", "Astro"],
    },
    {
      title: "Заглавие Едно",
      date: "Юли 2020",
      description: "Това ще бъде описанието на поста",
      link: "./first-article",
      tags: ["Svelte", "Data Science"],
    },
    {
      title: "Заглавие Две",
      date: "Юли 2020",
      link: "./first-article",
      description:
        "Това ще бъде описанието на поста. Тука още мъничко текст да видя, как ще изглежда",
      tags: ["SolidJS", "Astro"],
    },
  ];
</script>

<section id="posts">
  <h2>Здравей Свят</h2>
  <hr />
  <div class="posts">
    {#each posts as post}
      <div class="post">
        <a href={post.link}>
          <div>
            <div class="date">
              {post.date}
            </div>
            <div class="title">
              {post.title}
            </div>
            <div class="description">
              {post.description}
            </div>
          </div>
          <div>
            <div class="tags">
              {#each post.tags as tag}
                <div class="tag">{tag}</div>
              {/each}
            </div>
            <div class="lines">
              <hr />
              <hr />
            </div>
          </div>
        </a>
      </div>
    {/each}
  </div>
</section>

<style lang="scss">
  @import "../styles/breaking_points.scss";
  @import "../styles/colors.scss";

  #posts {
    hr {
      border-top-color: $black;
    }
    .posts {
      .post {
        filter: blur(0);
        box-sizing: border-box;
        margin-bottom: 3rem;
        margin-top: 2rem;
        transition: 0.8s;
        a {
          display: block;
          padding: 0 1rem;
          text-decoration: none;
          color: $black;
          .date {
            color: $font-grey;
            text-transform: uppercase;
            font-weight: 300;
            font-size: 0.9rem;
            letter-spacing: 0.25px;
            margin-bottom: 0.35rem;
          }
          .title {
            font-size: 1.4rem;
            font-weight: lighter;
            margin-bottom: 0.45rem;
          }
          .description {
            color: $font-grey;
            margin-bottom: 1.3rem;
          }
          .tags {
            display: flex;
            justify-content: end;
            .tag {
              padding: 0.25rem 0.5rem;
              background-color: rgb(55, 55, 55);
              color: $white;
              border-radius: 6px;
              margin-right: 0.5rem;
            }
          }
          .lines {
            position: relative;
            hr {
              position: absolute;
              &:nth-of-type(1) {
                border-top-color: $grey;
              }
              &:nth-of-type(2) {
                width: 0;
                z-index: 1;
                transition: 0.8s;
              }
            }
          }
        }
        &:hover .lines hr:nth-of-type(2) {
          width: 100%;
        }
      }
      &:hover {
        .post {
          filter: blur(3px);
          &:hover {
            filter: blur(0);
          }
        }
      }
      @include tablet {
        display: grid;
        grid-template-columns: 1fr 1fr;
        row-gap: 1rem;
        hr {
          margin-bottom: 1rem;
        }
        .post {
          margin: 0;
          a {
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            height: 10rem;

            .tags {
              margin-bottom: 1rem;
            }
            .lines {
              hr {
                margin: 0;
              }
            }
          }
        }
      }
    }
  }

  main.dark {
    #posts {
      .posts {
        a {
          color: $white;
          color: rgb(255, 255, 255);
        }
      }
      hr {
        border-top-color: rgba($white, 0.7);
      }
    }
  }
</style>
