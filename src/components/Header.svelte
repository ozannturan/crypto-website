<script>
    let tabs = [
      { name: 'Home', link: '#homepage' },
      { name: 'Price', link: '#price' } // Price sekmesine link ekleniyor
    ];
  
    let searchText = ''; // Arama metni için değişken
  </script>
  
  <header class="bg-white text-blue-700 p-4">
    <div class="container mx-auto flex justify-between items-center">
      <div class="text-2xl font-bold">
        <h1
          class="font-bold text-transparent bg-gradient-to-r bg-clip-text from-green-500 to-yellow-500"
        >
          <b>COIN</b>Web
        </h1>
      </div>
  
      <div class="flex items-center">
        <!-- Arama kutusu -->
        <input
          type="text"
          placeholder="Search..."
          class="border border-gray-300 px-4 py-2 rounded-md mr-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
          bind:value={searchText}
        />
  
        <nav class="flex items-center">
          <ul class="flex space-x-4">
            {#each tabs as tab}
              <li>
                <a
                  href={tab.link}
                  class="relative overflow-hidden px-5 py-2 group rounded-full bg-green-600 hover:scale-150
                      text-blue-700 hover:text-slate-950 transition-colors duration-200">{tab.name}</a
                >
              </li>
            {/each}
          </ul>
        </nav>
      </div>
    </div>
  </header>
  
