<script>
  import Modal from "svelte-mini-modal/lib/Modal.svelte";

  let open = false;

  const openModal = () => {
    open = true;
  };

  const closeModal = () => {
    open = false;
  };
</script>

<div>
  <button on:click={openModal}>open modal</button>

  <Modal
    {open}
    onClose={closeModal}
    className="fixed w-full h-full bg-black/60 z-50 inset-0 flex items-center justify-center"
    overlayClassName="absolute h-full w-full z-30"
  >
    <div class="w-4/5 bg-white p-8 z-50">
      <h1 class="text-left">hello world</h1>
    </div>
  </Modal>
</div>
