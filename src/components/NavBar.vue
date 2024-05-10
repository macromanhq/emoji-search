<template>
  <nav class="bg-gray-700">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="flex h-16 items-center justify-between">

        <div class="flex text-white">
          Emoji Search
        </div>
        <div class="flex items-center">
          <div class="md:block">
            <div class="ml-10 flex items-baseline space-x-4">
              <!-- Current: "bg-gray-900 text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white" -->
              <a href="https://github.com/macromanhq/emoji-search" class="text-white rounded-md px-3 py-2 text-sm font-medium"
                aria-current="page">
                <img src="/github.svg" class="inline w-6 h-6 text-white" alt="">
              </a>
              
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
}
</script>