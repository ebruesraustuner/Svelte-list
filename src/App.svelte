<script>
	let selected;
	$:console.log(selected)

  let isBack = false
  let list = [
    {
      name: 'teset',
      surname: 'testsur'
    },
    {
      name: 'teset2',
      surname: 'testsur2'
    }
  ]

  const toggleBackFront = (e) => {
    isBack = !isBack;
    // aynı kart tıklanırsa diye
    if (selected === Number(e.target.dataset.cardId)) {
			selected = null;
		} else {
			selected = Number(e.target.dataset.cardId)
		}
	}

</script>

<header>Plus Ultra</header>

{#each list as {name, surname}, i}
<button on:click={toggleBackFront} data-card-id={i}>Çevir {isBack}</button>
  <div class="card-list">
    <div class="card" class:show-back={selected === i}>
      <div class="card-front"  >
        front
      </div>
      <div class="card-back">
        back
        {name} , {surname}
      </div>
    </div>
  </div>
{/each}

<style>
  .card-list {
    background-color: transparent;
		width: 200px;
		height: 310px;
		margin: 0 20px 40px;
		border: 1px solid #f1f1f1;
		perspective: 1000px; /* Remove this if you don't want the 3D effect */

  }

  .card {
    position: relative;
		width: 100%;
		height: 100%;
		text-align: center;
		transition-duration: 2s;
		transform-style: preserve-3d;
  }
.show-back {
		transform: rotateY(180deg);
	}
  .card-front, .card-back {
		position: absolute;
		width: 100%;
		height: 100%;
		-webkit-backface-visibility: hidden; /* Safari */
		backface-visibility: hidden;
	}
  	/* Style the front side */
	.card-front {
		background-color: yellow;
	}

	/* Style the back side */
	.card-back {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		background-color: pink;
		width: 196px;
		height: 300px;
		transform: rotateY(180deg);
	}
</style>