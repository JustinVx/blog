<script>
  let password = ''
  const hash = s =>
    s.split('').reduce((a, b) => {
      a = (a << 5) - a + b.charCodeAt(0)
      return a & a
    }, 0)
//  $: console.log(password, hash(password))
</script>

{#if hash(password) === -1309148525}
  <slot />
{:else}
  <div class="max-w-none page mx-auto py-4 sm:py-8">
    <div class="flex flex-col sm:flex-row justify-between items-center mb-2 md:my-4 lg:my-6 lg:mb-8">
      <div class="order-1 sm:order-0 text-sm sm:text-base">
        <div>
          <p class="mb-2">
            Welcome! My website is protected with a password. If you have the password you can enter it below. Otherwise you can <a class="font-bold underline" href="mailto:request@justinvenbrux.nl">contact me</a> and ask for it. If that doesn't work you can always try brute forcing it. Don't worry, it's not that hard. ;)
          </p>
        </div>
      </div>
    </div>
    <div>
      <label for="password" class="text-xs text-gray-500 my-4 uppercase">Password:</label>
      <div class="grid grid-cols-4 gap-4">
        <input id="password" bind:value={password} type="password" class="col-span-4 sm:col-span-3 border-2 border-gray-300 p-2 rounded-lg" placeholder="Enter password over here" />
        <button class="bg-blue-500 text-white p-2 rounded-lg col-span-4 sm:col-span-1 hover:bg-blue-700 hover:text-white">Continue</button>
      </div>
    </div>
  </div>
{/if}