<script>
  import { Styles } from "sveltestrap";
  import { onMount } from "svelte";
  import {
    Button,
    Modal,
    ModalBody,
    ModalFooter,
    ModalHeader,
    Image,
    Toast,
    ToastHeader,
    ToastBody,
  } from "sveltestrap";

  let open = false;
  let isOpen = false;
  let showButton = true;
  let questions = [
    "Er Storm klog?",
    "Er Nikola flot?",
    "Er Storm lækker?",
    "Er Nikola stærk?",
    "Er Storm sej",
    "Er Nikola bedre end dig?",
    "Er Storm den bedste til Fortnite?",
    "Er Nikola smart?",

    "Bliver Storm 12 år?",
    "Spiller Nikola fodbold?",
    "Glæder drengene sig til i kommer?",
    "Bruger Nikola str 40 i sko?",
    "Spiller drengene Mordheim?",
    "Kan drengene godt lide at danse?",
    "Er Storm højere end Nikola?",
    "Håber drengene DU kommer?",
  ];
  //TODO: check emojis på storms telefon
  let count = 0;
  let replacements = [
    { l: "a", r: "💩" },
    { l: "b", r: "🚽" },
    //{ l: "c", r: "🐶" },
    { l: "d", r: "🥍" },
    { l: "e", r: "🪁" },
    { l: "f", r: "🤿" },
    { l: "g", r: "🥊" },
    { l: "h", r: "🏹" },
    { l: "i", r: "🎾" },
    { l: "j", r: "🏈" },
    { l: "k", r: "🏉" },
    { l: "l", r: "⚽️" },
    { l: "m", r: "🥬" },
    { l: "n", r: "🥦" },
    { l: "o", r: "🥑" },
    { l: "p", r: "🥝" },
    { l: "r", r: "🥭" },
    { l: "s", r: "🫐" },
    { l: "t", r: "🍏" },
    { l: "u", r: "🍎" },
    { l: "v", r: "🍋" },
    { l: "æ", r: "🍉" },
    { l: "ø", r: "🐯" },
    { l: "å", r: "🐨" },
    { l: "S", r: "🐻" },
    { l: "N", r: "🐼" },
    { l: "F", r: "🦊" },
    { l: "&", r: "🐰" },
    { l: "H", r: "🐭" },
    { l: "V", r: "🐱" },
    { l: "D", r: "🚙" },
    { l: "U", r: "🚨" },
    { l: "E", r: "🚠" },
  ];

  onMount(() => {
    const els = getElements();
    els.forEach((el) => {
      replacements.forEach((rep) => {
        el.textContent = el.textContent.replaceAll(rep.l, rep.r);
      });
    });
  });
  const toggle = () => {
    open = !open;
  };
  const toggleToast = () => {
    isOpen = !isOpen;
  };
  function getElements() {
    return document.querySelectorAll("p, h1, h2, h3,h4,h5,h6");
  }
  function toggleLetter() {
    window.location.href = "#main";
    open = !open;
    const els = getElements();
    els.forEach((el) => {
      const rep = replacements[count];
      el.textContent = el.textContent.replaceAll(rep.r, rep.l);
    });
    count = count + 1;
    els.forEach((el) => {
      const rep = replacements[count];
      el.textContent = el.textContent.replaceAll(rep.r, rep.l);
    });

    count = count + 1;
    if (count === 2) {
      isOpen = true;
    }
    if (count >= replacements.length) {
      showButton = false;
    }
  }
</script>

<Styles />
<div id="app">
  <Image alt="Nikola og Storm" src="./assets/drengene.jpg" />
  <Modal isOpen={open} {toggle}>
    <ModalHeader {toggle}>Modal title</ModalHeader>
    <ModalBody>
      {questions[count / 2 || 0]}
    </ModalBody>
    <ModalFooter>
      <Button color="primary" on:click={toggleLetter}>Ja</Button>
      <Button color="secondary" on:click={toggle}>Nej</Button>
    </ModalFooter>
  </Modal>
  <main id="main">
    {#if showButton}
      <div class="actions">
        <Button size="lg" class="help" color="danger" on:click={toggle}>
          HJÆLP!!!!!
        </Button>
      </div>
    {/if}
    <Toast {isOpen}>
      <ToastHeader>OK, her er lidt hjælp</ToastHeader>
      <ToastBody>
        <p>OK, du fik lidt hjælp.</p>
        <p>Jeg gav dig alle A'er og B'er</p>
        <p>Skal du have mere?</p>
        <Button color="primary" on:click={toggleToast}>Luk</Button>
      </ToastBody>
    </Toast>
    <h1>Storm &amp; Nikola holder fødselsdag!</h1>
    <h2>Fredag den 19/11</h2>
    <p>Hej alle sammen, så er det vores tur!</p>
    <p>Vi holder fødselsdagsfest den 19/11 og DU er inviteret.</p>
    <p>
      Vi mødes ved katten klokken 17 og går hjem til Storm på Ellekildevej 33,
      som også er der dine forældre kan hente dig når vi slutter igen klokken 20
    </p>
    <p>
      Vi byder selvfølgelig på noget mad, men hvis der er nget du ikke kan tåle
      vil vi meget gerne høre om det
    </p>
    <p>
      SU: senest den 12/11 til Storms far Jonas, på telefon <a
        href="tel:51923191">51 92 31 91</a
      >
    </p>
  </main>
</div>

<style>
</style>
