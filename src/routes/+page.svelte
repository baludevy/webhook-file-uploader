<script lang="ts">
    import Button3 from "../components/button3.svelte";
    import UploadIcon from "../icons/uploadIcon.svelte";

    const webhookUrl = "YOUR DISCORD WEBHOOK URL";

    async function handleUpload(event: Event) {
        const input = event.target as HTMLInputElement;
        if (!input.files?.[0]) return;

        const file = input.files[0];
        const formData = new FormData();
        formData.append("file", file);

        try {
            const response = await fetch(webhookUrl, {
                method: "POST",
                body: formData,
            });
        } catch {
            alert("failed to upload file");
        }
    }
</script>

<div class="flex h-screen justify-center items-center">
    <div class="align-center">
        <Button3 onClick={() => document.getElementById("fileInput")?.click()}>
            <div class="flex justify-center gap-2">
                <UploadIcon />
                Upload File
            </div>
        </Button3>
        <input
            id="fileInput"
            type="file"
            accept="*"
            class="hidden"
            on:change={handleUpload}
        />
    </div>
</div>

<style lang="css">
    :global(html) {
        background-color: #0a0a0a;
        color: #ffffff;
    }
</style>
