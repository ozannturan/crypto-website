<script lang="ts">
    import { onMount } from 'svelte';
  
    interface Crypto {
      name: string;
      symbol: string;
      current_price: number;
    }
  
    let cryptoData: Crypto[] = [];
  
    async function fetchCryptoData() {
      try {
        const response = await fetch(
          'https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=false'
        );
        cryptoData = await response.json();
      } catch (error) {
        console.error('Error fetching crypto data:', error);
      }
    }
  
    onMount(fetchCryptoData);
  </script>
  
  <main class="flex flex-col flex-1 p-4">
    <section id="homePage" class="grid grid-cols-1 lg:grid-cols-2 gap-10 py-8 sm:py-14">
      <div class="flex flex-col justify-center items-center lg:items-start text-center lg:text-left gap-6 md:gap-8 lg:gap-10">
        <h2 class="font-semibold text-4xl sm:text-5xl md:text-6xl">
          Welcome to <span class="text-green-500">CoinWeb</span> <br />Your Cryptocurrency Hub
        </h2>
        <p class="text-base sm:text-lg md:text-xl">
          <span class="text-green-500">
            Explore the world of cryptocurrencies with <span class="text-white">CoinWeb</span>.
          </span>
        </p>
      </div>
    </section>
  
    <section>
      <h2 class="text-2xl font-semibold mb-4">All Cryptocurrencies</h2>
      <table class="min-w-full divide-y divide-gray-200">
        <thead class="bg-gray-50">
          <tr>
            <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Name</th>
            <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Symbol</th>
            <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Price (USD)</th>
          </tr>
        </thead>
        <tbody class="bg-white divide-y divide-gray-200">
          {#each cryptoData as coin}
            <tr>
              <td class="px-6 py-4 whitespace-nowrap">
                <div class="flex items-center">
                  <div class="ml-4">
                    <div class="text-sm font-medium text-gray-900">{coin.name}</div>
                  </div>
                </div>
              </td>
              <td class="px-6 py-4 whitespace-nowrap">
                <div class="text-sm text-gray-900">{coin.symbol}</div>
              </td>
              <td class="px-6 py-4 whitespace-nowrap">
                <span class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800">
                  ${coin.current_price.toFixed(2)}
                </span>
              </td>
            </tr>
          {/each}
        </tbody>
      </table>
    </section>
  </main>