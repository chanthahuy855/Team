<template>
    <div class="relative">
      <div class="absolute inset-0 overflow-hidden">
        <div class="absolute -top-40 -right-40 w-80 h-80 bg-red-800/30 rounded-full mix-blend-multiply filter blur-3xl opacity-20"></div>
        <div class="absolute -bottom-40 -left-40 w-80 h-80 bg-red-600/20 rounded-full mix-blend-multiply filter blur-3xl opacity-20"></div>
      </div>
      
      <UPageSection>
        <div class="max-w-4xl mx-auto">
          <div class="relative backdrop-blur-xl bg-white/40 rounded-xl p-10 shadow-3xl overflow-hidden">      
            <div class="relative">
              <h1 class="text-4xl font-bold text-white mb-4 text-center">
                System Engineering Team
              </h1>
              <p class="text-lg text-gray-950 mb-5 text-center">
                Contact us if you want to automate your work and build innovative solutions with RPA.
              </p>
              <div class="flex flex-wrap justify-center">
                <UButton
                  to="#contact"
                  icon="i-lucide-arrow-right"
                  size="lg"
                  class="bg-gradient-to-r from-red-900 to-red-700 backdrop-blur-sm 
                         dark:bg-gradient-to-r dark:from-stone-900 dark:to-red-900  
                         hover:from-red-700 hover:to-red-700  
                         dark:hover:from-red-900 dark:hover:to-red-900 
                         transition-all duration-300 text-white shadow-lg
                         "
                >
                  Contact Us
                </UButton>
              </div>
            </div>
          </div>
        </div>
      </UPageSection>
    </div>

</template>