<script>
  import { bootcamps } from "$lib/data/bootcamps";
  import { tutorials } from "$lib/data/tutorials";
  
</script>

<ul class="test"> 
  <li class="dropdown nav-link"> Tutorials
    <ul class="dropdown-list">
      {#each tutorials as tutorial (tutorial.title)}
       <li class="dropdown-link">            
          <a class="nav-link" href={tutorial.href} sveltekit:prefetch>{tutorial.title}</a>            
       </li>          
      {/each}
    </ul>
  </li>
  {#each bootcamps as bootcamp (bootcamp.title)}
    {#if bootcamp.active}
      <li>
        <a class="nav-link" href={bootcamp.href} sveltekit:prefetch>{bootcamp.title}</a>
      </li>
    {/if}
  {/each}
  <li>
    <a class="nav-link" href="https://discord.com/invite/emeraldcity" target="_blank">Emerald City</a>
  </li>
  <slot/>
</ul>

<style>
  ul {
    display: flex;
    flex-direction: inherit;
    list-style-type: none;
    gap: 10px;
  }
  
  .nav-link {
    font-family: 'JetBrains Mono', monospace;
    font-size: 15px;
    color: var(--primary)
  }

  .test {
    position: relative;
  }

  .dropdown {
    position: relative;
    top: 2px;
    cursor: pointer;
    text-align: center;
    display:flex;
    justify-content: center;
  }

  .dropdown::after {
    content: "";
    width: 0;
    height: 0.2rem;
    border-radius: 10px;
    position: absolute;
    left: 0.3rem;
    bottom: 0.8rem;
    background-color: var(--primary);
    transition: width 0.2s ease;
  }

  .dropdown:hover::after {
    width: 87%;
  }

  .dropdown:hover ul, .dropdown:focus ul {
    opacity: 1;
    visibility: visible;
  }

  .dropdown-list {
    position: absolute;
    top: 2.8rem;
    width: 205px;
    box-shadow:0 0 10px rgb(36, 36, 36);
    background: var(--menu-bg);
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    padding: 0.5rem;
    opacity: 0;
    visibility: hidden;    
    transition: opacity 0.3s ease-in-out;
  }

  .dropdown-link {
    padding: 0.2rem 0.5rem;
    border-radius: 5px;
    transition: all 0.2s ease-in-out;
}
.dropdown-link:hover {
  background-color: var(--menu-hover);
}



</style>