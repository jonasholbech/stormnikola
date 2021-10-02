<script>
  import { Styles } from "sveltestrap";
  import {
    Button,
    Modal,
    ModalBody,
    ModalFooter,
    ModalHeader,
  } from "sveltestrap";
  let open = false;

  const toggle = () => {
    open = !open;
  };

  import { onMount } from "svelte";
  let questions = [
    "Er Storm klog?",
    "Er Nikola flot?",
    "Er Storm stærk?",
    "Er Nikola lækker?",
    "Er Storm sej",
    "Er Nikola bedre end dig?",
    "Er Storm den bedste til Fortnite?",
    "Er Nikola smart?",
    "Er Storm flot?",
    "Er Nikola stærk?",
    "Er Storm lækker?",
    "Er Nikola sej",
    "Er Storm bedre end dig?",
    "Er Nikola den bedste til Fortnite?",
    "Er Storm smart?",
    "Er Nikola klog?",
  ];
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
  console.log(replacements.length, questions.length);
  //
  onMount(() => {
    const els = getElements();
    els.forEach((el) => {
      replacements.forEach((rep) => {
        el.textContent = el.textContent.replaceAll(rep.l, rep.r);
      });
    });
  });
  function getElements() {
    return document.querySelectorAll("p, h1, h2, h3,h4,h5,h6");
  }
  function toggleLetter() {
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
  }
</script>

<Styles />
<div id="app">
  <div class="parallax" />
  <div class="actions">
    <Button size="lg" class="help" color="danger" on:click={toggle}
      >HJÆLP!!!!!</Button
    >
  </div>
  <!-- <div class="scroll-indicator">
  <div class="dots" />
</div> -->
  <!-- <div class="mouse">
    <div class="scrollWheel" />
  </div> -->
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
  <main>
    <h1>Storm &amp; Nikola holder fødselsdagsfest!</h1>
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
      SU: seneste den 12/11 til Storms far Jonas, på telefon <a
        href="tel:51923191">51 92 31 91</a
      >
    </p>
  </main>
</div>

<style>
</style>
