<script>
  let query = '';
  let photos = [];
    let acces_key = 'xoaEvHA2OfKpjkxVyjx0bbd74mSJAPX56IjPT01AgEc';

  async function fetchPhotos(query) {
    const response = await fetch(`https://api.unsplash.com/search/photos?query=${query}&per_page=30&client_id=${acces_key}`);
    const data = await response.json();
    photos = data.results;
  }

  function handleSearch(event) {
    event.preventDefault();
    fetchPhotos(query);
  }
  fetchPhotos('funny dog');
</script>



<h1>Wyszukiwarka zdjęć</h1>

<form on:submit={handleSearch}>
<input class="searchBar" type="text" bind:value={query} placeholder="">
  <button class="button" type="submit">Search</button>
</form>
<div class="photo-grid">
  {#each photos as photo}
    <img class="photo" src={photo.urls.thumb} alt={photo.alt_description}>
  {/each}
</div>



<style>
  .searchBar{
    width: 300px;
    height: 20px;
    border-radius: 10px;
    font-size: 16px;
    color: dimgray;
    padding: 10px;
  }

  .photo-grid {
    margin-top: 40px;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
  }

  .photo {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }

  .button{
    margin-left: 10px;
    background-color: gold;
    color: #fff;
    padding: 11px;
  }

</style>
