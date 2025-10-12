<script lang="ts">
    import ClockDigit from "./ClockDigit.svelte";

    let date = $state([0, 0, 0, 0, 0, 0])

    const update = () => {
        date = new Date().toLocaleString([], {
            hour: '2-digit',
            minute: '2-digit',
            second: '2-digit',
            hour12: false,
        }).split('').filter(c => "1234567890".split("").includes(c)).map(Number)
    }

    setInterval(update, 100)

    update()
</script>

<div class="w-screen">
    <main class="h-screen flex flex-row items-center justify-center bg-neutral-950 gap-8 px-20">
        <div class="flex flex-row border-4 border-white/20 w-1/3 gap-4 p-4">
            <ClockDigit n={date[0]}/>
            <ClockDigit n={date[1]}/>
        </div>
        <div class="flex flex-row border-4 border-white/20 w-1/3 gap-4 p-4">
            <ClockDigit n={date[2]}/>
            <ClockDigit n={date[3]}/>
        </div>
        <div class="flex flex-row border-4 border-white/20 w-1/3 gap-4 p-4">
            <ClockDigit n={date[4]}/>
            <ClockDigit n={date[5]}/>
        </div>
    </main>
</div>

<style>
</style>
