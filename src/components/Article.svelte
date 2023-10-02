<script>
    export let title = '';
    export let image = '';
    export let image_alt = '';
    export let content = '';
    export let link = '';
    export let credit = '';
</script>

<!-- Markup -->
<div class="article-card max-w-md border border-gray-200 rounded-md shadow-lg p-4 mx-2 mb-4 transition-transform transform hover:scale-105 duration-300 ease-in-out">
    <div class="flex">
        <a href={link} target="_blank" class="flex w-full">
            <div class="flex-initial">
                <div class="w-48 h-36 pr-4">
                    <img class="w-full h-full object-cover rounded" src={image} alt={image_alt} />
                </div>
                <h1 class="text-xl text-white font-semibold mb-2 line-clamp-2">{title}</h1>
                <p class="mt-2 text-sm text-gray-300 line-clamp-3">{content}</p>
                <p class="text-xs text-gray-400 mt-2">Credit: {credit}</p>
            </div>
        </a>
    </div>
</div>
<!-- /Markup -->

<style lang="postcss">
/* Additional styling */

/* Add custom class for text truncation */
.line-clamp-2 {
    display: -webkit-box;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
    -webkit-line-clamp: 2; /* Limit to 2 lines */
}

.line-clamp-3 {
    display: -webkit-box;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
    -webkit-line-clamp: 5;
}
</style>
