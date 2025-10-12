<script lang="ts">
    const {n} = $props()

    const nStr = $derived(n.toString())

    const BL = [90, 180]
    const BR = [0, 90]
    const TL = [180, 270]
    const TR = [270, 0]
    const LR = [0, 180]
    const TB = [90, 270]
    const NO = [135, 135]

    const DIGITS = {
        1: [
            BR, LR, BL, NO,
            TR, BL, TB, NO,
            NO, TB, TB, NO,
            NO, TB, TB, NO,
            BR, TL, TR, BL,
            TR, LR, LR, TL
        ],
        2: [
            BR, LR, LR, BL,
            TR, LR, BL, TB,
            BR, LR, TL, TB,
            TB, BR, LR, TL,
            TB, TR, LR, BL,
            TR, LR, LR, TL
        ],
        3: [
            BR, LR, LR, BL,
            TR, LR, BL, TB,
            BR, LR, TL, TB,
            TR, LR, BL, TB,
            BR, LR, TL, TB,
            TR, LR, LR, TL
        ],
        4: [
            BR, BL, BR, BL,
            TB, TB, TB, TB,
            TB, TR, TL, TB,
            TR, LR, BL, TB,
            NO, NO, TB, TB,
            NO, NO, TR, TL
        ],
        5: [
            BR, LR, LR, BL,
            TB, BR, LR, TL,
            TB, TR, LR, BL,
            TR, LR, BL, TB,
            BR, LR, TL, TB,
            TR, LR, LR, TL
        ],
        6: [
            BR, LR, LR, BL,
            TB, BR, LR, TL,
            TB, TR, LR, BL,
            TB, BR, BL, TB,
            TB, TR, TL, TB,
            TR, LR, LR, TL
        ],
        7: [
            BR, LR, LR, BL,
            TR, LR, BL, TB,
            NO, NO, TB, TB,
            NO, NO, TB, TB,
            NO, NO, TB, TB,
            NO, NO, TR, TL
        ],
        8: [
            BR, LR, LR, BL,
            TB, BR, BL, TB,
            TB, TR, TL, TB,
            TB, BR, BL, TB,
            TB, TR, TL, TB,
            TR, LR, LR, TL
        ],
        9: [
            BR, LR, LR, BL,
            TB, BR, BL, TB,
            TB, TR, TL, TB,
            TR, LR, BL, TB,
            BR, LR, TL, TB,
            TR, LR, LR, TL
        ],
        0: [
            BR, LR, LR, BL,
            TB, BR, BL, TB,
            TB, TB, TB, TB,
            TB, TB, TB, TB,
            TB, TR, TL, TB,
            TR, LR, LR, TL
        ],
    } as { [key: string]: number[][] }
</script>

<div class="grid grid-cols-4 grid-rows-6 w-1/2 gap-1">
    {#each Array(4*6) as _, i}
        <div class="border-2 border-white/10 relative aspect-square *:transition">
            <div class="w-[calc(1/2*100%+2px)] h-1 bg-red-500 absolute top-0 bottom-0 my-auto right-0 origin-[2px_2px] rounded-l-full" style={`transform: rotate(${DIGITS[nStr][i][0]}deg)`}></div>
            <div class="w-[calc(1/2*100%+2px)] h-1 bg-red-500 absolute top-0 bottom-0 my-auto right-0 origin-[2px_2px] rounded-l-full" style={`transform: rotate(${DIGITS[nStr][i][1]}deg)`}></div>
        </div>
    {/each}
</div>
