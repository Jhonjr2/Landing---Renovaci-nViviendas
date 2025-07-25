<script lang="ts" setup>
import { ref } from "vue";

import { useColorMode } from "@vueuse/core";
const mode = useColorMode();
mode.value = "light";

import {
  NavigationMenu,
  NavigationMenuContent,
  NavigationMenuItem,
  NavigationMenuLink,
  NavigationMenuList,
  NavigationMenuTrigger,
} from "@/components/ui/navigation-menu";
import {
  Sheet,
  SheetContent,
  // SheetFooter,
  SheetHeader,
  SheetTitle,
  SheetTrigger,
} from "@/components/ui/sheet";

import { Button } from "@/components/ui/button";
// import { Separator } from "@/components/ui/separator";

import { ChevronsDown, Menu } from "lucide-vue-next";
import ToggleTheme from "./ToggleTheme.vue";
import WhatsAppIcon from "@/icons/WhatsAppIcon.vue";

interface RouteProps {
  href: string;
  label: string;
}

interface FeatureProps {
  title: string;
  description: string;
}

const routeList: RouteProps[] = [
  {
    href: "#servicios",
    label: "Servicios",
  },
  {
    href: "#proyectos",
    label: "Proyectos",
  },
  {
    href: "#contact",
    label: "Contacto",
  },
  {
    href: "#faq",
    label: "FAQ",
  },
];

const featureList: FeatureProps[] = [
 {
   title: "Diseño Personalizado",
   description: "Creamos espacios únicos que reflejan tu estilo y se adaptan perfectamente a tus necesidades.",
 },
 {
   title: "Calidad Garantizada",
   description: "Trabajamos con materiales premium y profesionales certificados para resultados duraderos.",
 },
 {
   title: "Proyecto Completo",
   description: "Desde el diseño 3D hasta la entrega final, nos encargamos de cada detalle de tu renovación.",
 },
];

const isOpen = ref<boolean>(false);
</script>

<template>
  <header
    :class="{
      // 'shadow-light': mode === 'light',
      // 'shadow-dark': mode === 'dark',
      'w-[90%] md:w-[70%] lg:w-[75%] lg:max-w-screen-xl top-5 mx-auto sticky border z-40 rounded-2xl flex justify-between items-center p-2 bg-card shadow-md': true,
    }"
  >
  <a href="/" class="logo" style="display: flex; align-items: center; gap: 8px;">
  <img src="../assets/img/logo1.ico" alt="Logo"
       style="height: 40px; width: 40px; border-radius: 8px; object-fit: cover;" />
  <span style="font-weight: bold;" :class="mode === 'light' ? 'text-transparent bg-gradient-to-r from-[#1A8ACC] to-[#9C27B0] bg-clip-text' : 'text-transparent bg-gradient-to-r from-[#1A8ACC] to-white bg-clip-text'"
  >Viviendas</span>
</a>

    <!-- Mobile -->
    <div class="flex items-center lg:hidden">
      <Sheet v-model:open="isOpen">
        <SheetTrigger as-child>
          <Menu
            @click="isOpen = true"
            class="cursor-pointer"
          />
        </SheetTrigger>

        <SheetContent
          side="left"
          class="flex flex-col justify-between rounded-tr-2xl rounded-br-2xl bg-card"
        >
          <div>
            <SheetHeader class="mb-4 ml-4">
              <SheetTitle class="flex items-center">
                <a
                  href="/"
                  class="flex items-center"
                >
                  <ChevronsDown
                    class="bg-gradient-to-tr from-primary/70 via-primary to-primary/70 rounded-lg size-9 mr-2 border text-white"
                  />
                  Viviendas
                </a>
              </SheetTitle>
            </SheetHeader>

            <div class="flex flex-col gap-2">
              <Button
                v-for="{ href, label } in routeList"
                :key="label"
                as-child
                variant="ghost"
                class="justify-start text-base"
              >
                <a
                  @click="isOpen = false"
                  :href="href"
                >
                  {{ label }}
                </a>
              </Button>
            </div>
          </div>

          <!-- <SheetFooter class="flex-col sm:flex-col justify-start items-start">
            <Separator class="mb-2" />

            <ToggleTheme />
          </SheetFooter> -->
        </SheetContent>
      </Sheet>
    </div>

    <!-- Desktop -->
    <NavigationMenu class="hidden lg:block">
      <NavigationMenuList>
        <NavigationMenuItem>
          <NavigationMenuTrigger class="bg-card text-base">
            Soluciones
          </NavigationMenuTrigger>
          <NavigationMenuContent>
            <div class="grid w-[600px] grid-cols-2 gap-5 p-4">
              <img
                src="../assets/img/img4.jpg"
                alt="Beach"
                class="h-full w-full rounded-md object-cover"
              />
              <ul class="flex flex-col gap-2">
                <li
                  v-for="{ title, description } in featureList"
                  :key="title"
                  class="rounded-md p-2 text-sm hover:bg-muted"
                >
                  <p class="mb-1 font-semibold leading-none text-foreground">
                    {{ title }}
                  </p>
                  <p class="text-muted-foreground leading-relaxed">
                    {{ description }}
                  </p>
                </li>
              </ul>
            </div>
          </NavigationMenuContent>
        </NavigationMenuItem>

        <NavigationMenuItem>
          <NavigationMenuLink asChild>
            <Button
              v-for="{ href, label } in routeList"
              :key="label"
              as-child
              variant="ghost"
              class="justify-start text-base"
            >
              <a :href="href">
                {{ label }}
              </a>
            </Button>
          </NavigationMenuLink>
        </NavigationMenuItem>
      </NavigationMenuList>
    </NavigationMenu>

    <div class="hidden lg:flex">
      <!-- <ToggleTheme /> -->

      <Button
        as-child
        size="sm"
        variant="ghost"
        aria-label="View on WhatsApp"
      >
        <a
          aria-label="View on WhatsApp"
          href="https://wa.me/573116164386?text=Hola%2C%20estoy%20interesado%20en%20renovar%20mi%20vivienda%20y%20quisiera%20más%20información."
          target="_blank"
        >
          <WhatsAppIcon class="size-5" />
        </a>
      </Button>
    </div>
  </header>
</template>

<style scoped>
.shadow-light {
  box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.085);
}

.shadow-dark {
  box-shadow: inset 0 0 5px rgba(255, 255, 255, 0.141);
}
</style>
