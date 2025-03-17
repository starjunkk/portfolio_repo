<script>
    export let title;
    export let description;
    export let image;
    export let tags;
</script>

<div class="work-item">
    <div class="image">
        <img src={image} alt={title} on:error={() => image = 'https://via.placeholder.com/1920x300?text=Image+Not+Found'} />
    </div>
    <div class="text-content">
        <h2>{title}</h2>
        <p class="description">{description}</p>
        <div class="tags">
            {#each tags as tag}
                <span class="tag">{tag}</span>
            {/each}
        </div>
    </div>
</div>

<style>
    .work-item {
        width: 100%;
        background-color: #222;
        border-radius: 8px;
        box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
        margin-bottom: 20px;
        color: white;
        overflow: hidden;
    }

    .image {
        width: 100vw;
        height: 300px;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #181818;
    }

    .image img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        display: block;
    }

    .text-content {
        padding: 20px;
        text-align: left;
    }

    h2 {
        margin-bottom: 10px;
        font-size: 1.8rem;
        font-weight: bold;
        color: #fff; /* Testo bianco puro */
    }

    .description {
        font-size: 1.2rem;
        color: #f1f1f1; /* Testo più chiaro per migliore leggibilità */
        margin-bottom: 10px;
    }

    .tags {
        margin-top: 10px;
        display: flex;
        gap: 10px;
        flex-wrap: wrap;
    }

    .tag {
        background-color: #ff5722;
        color: white;
        padding: 5px 12px;
        border-radius: 15px;
        font-size: 0.9rem;
        font-weight: bold;
    }
</style>
