<script>
    import { onMount } from "svelte";
    import TimeSlot from "./TimeSlot.svelte";

    let data = []; // 用于存储从 API 返回的时间段数据。
	let loading = true; // 表示数据是否正在加载，默认是 true。
	let error = null; // 用于存储任何错误信息，默认是 null。

    const apiUrl = 'http://localhost:3015/api/v1/timeslots/';

    // 当组件挂载时，发送异步请求
    onMount(async()=>{
        try {
            const response = await fetch(apiUrl);  // 向 API 发送请求
            if (!response.ok){
                throw new Error('Failed to fetch data'); // 如果请求失败，抛出错误
            }
            data = await response.json(); // 将响应转换为 JSON 并存储
            console.log(data);
        } catch(err) {
            error = err.message; // 捕获错误信息
        } finally {
            loading = false; // 请求结束后，设为false
        }
    });
</script>

<!-- 显示加载状态 -->
{#if loading}
	<p>Loading...</p>
{/if}

<!-- 显示错误信息 -->
{#if error}
	<p>Error: {error}</p>
{/if}

<!-- 如果数据成功加载，循环渲染每个时间段 -->
{#if !loading && !error}
	<div class="grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-4">
		{#each data.data as item}
			<TimeSlot timeslotUrl={item} />
		{/each}
	</div>
{/if}