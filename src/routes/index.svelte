<script>
  let content = {
    mode: "read",
    dictionary: [
      { id: 1, title: "HTML", desc: "HTML is ..." },
      { id: 2, title: "CSS", desc: "CSS is ..." },
      { id: 3, title: "JavaScript", desc: "JavaScript is ..." },
    ],
    selectedId: 2,
    maxId: 3,
  };

  let explanation = "";
  let item = {};

  $: {
    if (content.mode === "read") {
      item = content.dictionary.find((dict) => dict.id === content.selectedId);
      explanation = `<h2>${item.title}</h2><p>${item.desc}</p>`;
    }
  }

  const handleId = (e) => {
    content.selectedId = e.target.dataset.item;
    console.log(content.selectedId);
    content.mode = "read";
    content = content;
  };
</script>

<ul>
  {#each content.dictionary as dict (dict.id)}
    <li>
      <a
        href="/dict/${dict.title.toLowerCase()}"
        data-item={dict.id}
        on:click|preventDefault={(e) => handleId(e)}>{dict.title}</a
      >
    </li>
  {/each}
</ul>

<p>{@html explanation}</p>
