<script>
  export let awards = [
    { award: "1st Place HackAUBG4", year: 2022, url: "./first-article" },
    { award: "3-то място АМТИЗ", year: 2022, url: "./first-article" },
  ];
</script>

<section id="awards">
  <h2>Здравей свят</h2>
  <hr />
  <div class="awards">
    {#each awards as award}
      <a href={award.url}>
        <div class="award">
          <h3>{award.award}</h3>
          <span>{award.year}</span>
          <div class="lines">
            <hr />
            <hr />
          </div>
        </div>
      </a>
    {/each}
  </div>
</section>

<style lang="scss">
  @import "../styles/breaking_points.scss";
  @import "../styles/colors.scss";
  #awards {
    hr {
      border-top-color: $black;
    }
    .awards {
      padding: 0 0.5rem;
      a {
        text-decoration: none;
        color: $black;
        .award {
          position: relative;
          display: flex;
          align-items: center;
          justify-content: space-between;
          transition: 0.3s;
          h3,
          span {
            font-size: 1.4rem;
            @include desktop {
              font-size: 1.6rem;
            }
          }

          .lines {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            hr {
              position: absolute;
              margin: 0;
              transition: 0.7s;

              &:nth-of-type(1) {
                z-index: 1;
                border-top-color: $grey;
              }
              &:nth-of-type(2) {
                z-index: 2;
                border-top-color: $black;
                width: 0;
              }
            }
          }
        }
      }
      &:hover {
        .award {
          color: $grey;
          filter: blur(1px);
          &:hover {
            color: $black;
            filter: blur(0);
            hr {
              &:nth-last-of-type(2) {
                width: 100%;
              }
            }
          }
        }
      }
    }
  }

  main.dark #awards {
    hr {
      &:nth-of-type(2) {
        border-top-color: $white;
      }
    }
    a {
      color: $white;
      .awards:hover {
        .award:hover {
          color: $white;
        }
      }
    }
  }
</style>
