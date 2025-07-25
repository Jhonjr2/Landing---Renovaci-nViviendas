<script setup lang="ts">
import {
  Card,
  CardDescription,
  CardHeader,
  CardTitle,
} from "@/components/ui/card";

enum ProService {
  YES = 1,
  NO = 0,
}

interface ServiceProps {
  title: string;
  pro: ProService;
  description: string;
}

const serviceList: ServiceProps[] = [
  {
    title: "Diseño Personalizado",
    description:
      "Creamos espacios únicos que reflejan tu estilo y necesidades, desde la idea inicial hasta el último detalle.",
    pro: 1,
  },
  {
    title: "Asesoría en Materiales",
    description:
      "Te guiamos en la elección de materiales de alta calidad, funcionales y estéticos para cada espacio.",
    pro: 0,
  },
  {
    title: "Remodelaciones Integrales",
    description:
      "Transformamos cocinas, baños y espacios completos con soluciones eficientes y modernas.",
    pro: 1,
  },
  {
    title: "Gestión de Proyectos",
    description:
      "Nos encargamos de todo el proceso de renovación para que tú no tengas que preocuparte por nada.",
    pro: 0,
  },
];

</script>

<template>
  <section id="servicios" class="container py-24 sm:py-32">
    <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
      Servicios
    </h2>

    <h2 class="text-3xl md:text-4xl text-center font-bold mb-4">
      Mejora tu hogar con expertos
    </h2>

    <h3 class="md:w-1/2 mx-auto text-xl text-center text-muted-foreground mb-8">
      Soluciones personalizadas en diseño, remodelación y acabados para renovar tu espacio y aumentar el valor de tu
      propiedad.
    </h3>

    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4"></div>

    <div class="grid sm:grid-cols-2 lg:grid-cols-2 gap-4 w-full lg:w-[60%] mx-auto">
      <div v-for="{ title, description } in serviceList" :key="title">
        <Card class="bg-muted/60 dark:bg-card h-full relative">
          <CardHeader>
            <CardTitle>{{ title }}</CardTitle>
            <CardDescription>{{ description }}</CardDescription>
          </CardHeader>
        </Card>
      </div>
    </div>
  </section>
</template>
