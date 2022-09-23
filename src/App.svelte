<script>

  const uid = () => {
    return Date.now().toString(36) + Math.random().toString(36).substr(2);
  };
  const initialBlock = [
    { id: uid(), html: "This is a paragraph text", tag: "p" },
    { id: uid(), html: "This is a Heading 1", tag: "h1" },
  ];
</script>

<main>
  <ul>
    {#each initialBlock as block}
      <svelte:element this={block.tag} id={block.id} contenteditable="true"
        >{block.html}
      </svelte:element>
    {/each}
  </ul>
</main>
