<script lang="ts">
    import { FeedbackStore } from "../stores/feedback";

    import Card from "./Card.svelte";
    export let item;

    const handleDelete = (itemId: number) => {
        FeedbackStore.update((currentFeedbackList) => {
            return currentFeedbackList.filter((item) => item.id != itemId);
        });
    };
</script>

<Card>
    <div class="num-display">
        {item.rating}
    </div>
    <button class="close" on:click={() => handleDelete(item.id)}>x</button>
    <p class="text-display">
        {item.comment}
    </p>
</Card>

<style>
    .num-display {
        position: absolute;
        top: -10px;
        left: -10px;
        width: 50px;
        color: #fff;
        border-radius: 50%;
        padding: 10px;
        text-align: center;
        background-color: rgb(157, 63, 219);
        font-size: 19px;
        box-shadow: 5px 6px 9px 2px rgba(0, 0, 0, 0.03);
        -webkit-box-shadow: 5px 6px 9px 2px rgba(0, 0, 0, 0.03);
        -moz-box-shadow: 5px 6px 9px 2px rgba(0, 0, 0, 0.03);
    }

    .close {
        position: absolute;
        top: 10px;
        right: 20px;
        cursor: pointer;
        background: none;
        border: none;
        font-size: 25px;
        font-weight: 600;
    }
</style>
