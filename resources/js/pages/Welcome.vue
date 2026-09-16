<script setup lang="ts">
import { Head, Link, usePage } from '@inertiajs/vue3';
import {
    ArrowRight,
    BarChart3,
    Bot,
    CheckCircle2,
    ChevronRight,
    DatabaseZap,
    Layers3,
    LockKeyhole,
    Menu,
    Sparkles,
    X,
} from '@lucide/vue';
import { computed, ref } from 'vue';
import { dashboard, login, register } from '@/routes';

const page = usePage();
const menuOpen = ref(false);

const dashboardUrl = computed(() =>
    page.props.currentTeam ? dashboard(page.props.currentTeam.slug).url : '/',
);

const navItems = [
    { label: 'Soluciones', href: '#solutions' },
    { label: 'Proceso', href: '#process' },
    { label: 'Resultados', href: '#results' },
];

const capabilities = [
    {
        icon: Bot,
        title: 'Automatizacion inteligente',
        description:
            'Flujos que reducen tareas manuales y conectan areas comerciales, operativas y administrativas.',
    },
    {
        icon: DatabaseZap,
        title: 'Datos accionables',
        description:
            'Dashboards, integraciones y modelos que convierten informacion dispersa en decisiones claras.',
    },
    {
        icon: Layers3,
        title: 'Software a la medida',
        description:
            'Aplicaciones web modernas, escalables y alineadas con la forma real de trabajar de tu equipo.',
    },
];

const process = [
    'Mapeamos la operacion y priorizamos los puntos de mayor impacto.',
    'Disenamos prototipos rapidos para validar experiencia, datos y flujo.',
    'Construimos, medimos y mejoramos con entregas cortas y trazables.',
];

const metrics = [
    { value: '35%', label: 'menos tiempo operativo en procesos repetitivos' },
    { value: '3x', label: 'mas visibilidad para tomar decisiones semanales' },
    { value: '24/7', label: 'sistemas disponibles para equipos y clientes' },
];
</script>

<template>
    <Head title="Revolutiva">
        <meta
            name="description"
            content="Revolutiva crea automatizacion, datos y software a la medida para empresas que quieren operar mejor."
        />
    </Head>

    <main class="min-h-screen bg-[#f7f4ef] text-[#16201d]">
        <section class="relative overflow-hidden bg-[#10211d] text-white">
            <div
                class="absolute inset-0 bg-[radial-gradient(circle_at_70%_20%,rgba(63,203,143,0.24),transparent_34%),linear-gradient(135deg,rgba(16,33,29,0.98),rgba(21,48,43,0.92))]"
            />
            <div class="relative mx-auto flex min-h-[92vh] max-w-7xl flex-col px-5 sm:px-8">
                <header class="flex items-center justify-between py-5">
                    <a href="#" class="flex items-center gap-3" aria-label="Revolutiva">
                        <span
                            class="grid h-10 w-10 place-items-center rounded-md bg-[#3fcb8f] text-lg font-black text-[#0e211c]"
                        >
                            R
                        </span>
                        <span class="text-lg font-semibold tracking-wide">Revolutiva</span>
                    </a>

                    <nav class="hidden items-center gap-8 text-sm text-white/78 md:flex">
                        <a
                            v-for="item in navItems"
                            :key="item.href"
                            :href="item.href"
                            class="transition hover:text-white"
                        >
                            {{ item.label }}
                        </a>
                    </nav>

                    <div class="hidden items-center gap-3 md:flex">
                        <Link
                            v-if="$page.props.auth.user"
                            :href="dashboardUrl"
                            class="inline-flex items-center gap-2 rounded-md border border-white/18 px-4 py-2 text-sm font-medium text-white transition hover:border-white/40"
                        >
                            Dashboard
                            <ChevronRight class="h-4 w-4" />
                        </Link>
                        <template v-else>
                            <Link
                                :href="login()"
                                class="rounded-md px-4 py-2 text-sm font-medium text-white/80 transition hover:text-white"
                            >
                                Ingresar
                            </Link>
                            <Link
                                :href="register()"
                                class="inline-flex items-center gap-2 rounded-md bg-[#3fcb8f] px-4 py-2 text-sm font-semibold text-[#0e211c] transition hover:bg-[#65d9a6]"
                            >
                                Empezar
                                <ArrowRight class="h-4 w-4" />
                            </Link>
                        </template>
                    </div>

                    <button
                        type="button"
                        class="grid h-10 w-10 place-items-center rounded-md border border-white/15 text-white md:hidden"
                        aria-label="Abrir menu"
                        @click="menuOpen = !menuOpen"
                    >
                        <X v-if="menuOpen" class="h-5 w-5" />
                        <Menu v-else class="h-5 w-5" />
                    </button>
                </header>

                <div
                    v-if="menuOpen"
                    class="rounded-md border border-white/12 bg-white/8 p-4 backdrop-blur md:hidden"
                >
                    <a
                        v-for="item in navItems"
                        :key="item.href"
                        :href="item.href"
                        class="block py-3 text-sm text-white/82"
                        @click="menuOpen = false"
                    >
                        {{ item.label }}
                    </a>
                    <Link
                        :href="$page.props.auth.user ? dashboardUrl : login()"
                        class="mt-3 inline-flex w-full items-center justify-center gap-2 rounded-md bg-[#3fcb8f] px-4 py-3 text-sm font-semibold text-[#0e211c]"
                    >
                        {{ $page.props.auth.user ? 'Dashboard' : 'Ingresar' }}
                        <ArrowRight class="h-4 w-4" />
                    </Link>
                </div>

                <div class="grid flex-1 items-center gap-12 py-14 lg:grid-cols-[1.04fr_0.96fr]">
                    <div class="max-w-3xl">
                        <div
                            class="mb-7 inline-flex items-center gap-2 rounded-md border border-white/14 bg-white/8 px-3 py-2 text-sm text-white/82"
                        >
                            <Sparkles class="h-4 w-4 text-[#3fcb8f]" />
                            Transformacion digital con foco operativo
                        </div>
                        <h1 class="max-w-4xl text-5xl font-semibold leading-[1.02] sm:text-6xl lg:text-7xl">
                            Software, datos y automatizacion para empresas que quieren avanzar.
                        </h1>
                        <p class="mt-6 max-w-2xl text-lg leading-8 text-white/72">
                            Revolutiva disena y construye soluciones digitales que eliminan friccion,
                            ordenan la informacion y convierten procesos complejos en sistemas simples
                            de operar.
                        </p>
                        <div class="mt-9 flex flex-col gap-3 sm:flex-row">
                            <Link
                                :href="$page.props.auth.user ? dashboardUrl : register()"
                                class="inline-flex items-center justify-center gap-2 rounded-md bg-[#3fcb8f] px-6 py-3 text-sm font-bold text-[#0e211c] transition hover:bg-[#65d9a6]"
                            >
                                {{ $page.props.auth.user ? 'Ir al dashboard' : 'Crear cuenta' }}
                                <ArrowRight class="h-4 w-4" />
                            </Link>
                            <a
                                href="#solutions"
                                class="inline-flex items-center justify-center gap-2 rounded-md border border-white/18 px-6 py-3 text-sm font-semibold text-white transition hover:border-white/42"
                            >
                                Ver soluciones
                                <ChevronRight class="h-4 w-4" />
                            </a>
                        </div>
                    </div>

                    <div class="relative">
                        <div class="rounded-md border border-white/14 bg-white/10 p-5 shadow-2xl backdrop-blur">
                            <div class="mb-6 flex items-center justify-between">
                                <div>
                                    <p class="text-sm text-white/56">Panel operativo</p>
                                    <h2 class="text-xl font-semibold">Crecimiento controlado</h2>
                                </div>
                                <BarChart3 class="h-7 w-7 text-[#3fcb8f]" />
                            </div>
                            <div class="space-y-4">
                                <div
                                    v-for="metric in metrics"
                                    :key="metric.value"
                                    class="rounded-md bg-[#f7f4ef] p-5 text-[#16201d]"
                                >
                                    <p class="text-3xl font-black">{{ metric.value }}</p>
                                    <p class="mt-1 text-sm leading-6 text-[#53635e]">{{ metric.label }}</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="solutions" class="mx-auto max-w-7xl px-5 py-20 sm:px-8">
            <div class="max-w-3xl">
                <p class="text-sm font-bold uppercase tracking-[0.18em] text-[#25775a]">Soluciones</p>
                <h2 class="mt-3 text-4xl font-semibold leading-tight text-[#16201d]">
                    Tecnologia hecha para la operacion, no para el cajon de ideas.
                </h2>
            </div>
            <div class="mt-10 grid gap-5 md:grid-cols-3">
                <article
                    v-for="capability in capabilities"
                    :key="capability.title"
                    class="rounded-md border border-[#dfd7cb] bg-white p-6 shadow-sm"
                >
                    <component :is="capability.icon" class="h-8 w-8 text-[#25775a]" />
                    <h3 class="mt-7 text-xl font-semibold">{{ capability.title }}</h3>
                    <p class="mt-3 text-sm leading-7 text-[#53635e]">{{ capability.description }}</p>
                </article>
            </div>
        </section>

        <section id="process" class="bg-white">
            <div class="mx-auto grid max-w-7xl gap-10 px-5 py-20 sm:px-8 lg:grid-cols-[0.8fr_1.2fr]">
                <div>
                    <p class="text-sm font-bold uppercase tracking-[0.18em] text-[#25775a]">Proceso</p>
                    <h2 class="mt-3 text-4xl font-semibold leading-tight">
                        De problema visible a sistema funcionando.
                    </h2>
                </div>
                <div class="space-y-4">
                    <div
                        v-for="(step, index) in process"
                        :key="step"
                        class="flex gap-5 rounded-md border border-[#e8e0d6] bg-[#fbfaf7] p-5"
                    >
                        <span
                            class="grid h-9 w-9 shrink-0 place-items-center rounded-md bg-[#17372f] text-sm font-bold text-white"
                        >
                            {{ index + 1 }}
                        </span>
                        <p class="self-center leading-7 text-[#42534d]">{{ step }}</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="results" class="mx-auto max-w-7xl px-5 py-20 sm:px-8">
            <div class="rounded-md bg-[#17372f] p-7 text-white sm:p-10 lg:p-12">
                <div class="grid gap-10 lg:grid-cols-[1fr_0.8fr] lg:items-center">
                    <div>
                        <p class="text-sm font-bold uppercase tracking-[0.18em] text-[#8ae4b8]">Resultados</p>
                        <h2 class="mt-3 text-4xl font-semibold leading-tight">
                            Menos friccion, mas trazabilidad y mejores decisiones.
                        </h2>
                        <p class="mt-5 max-w-2xl leading-8 text-white/72">
                            Construimos con una mirada integral: experiencia de usuario, arquitectura,
                            seguridad y medicion continua para que cada entrega tenga impacto real.
                        </p>
                    </div>
                    <div class="space-y-4">
                        <div class="flex items-start gap-3">
                            <CheckCircle2 class="mt-1 h-5 w-5 shrink-0 text-[#8ae4b8]" />
                            <p class="text-white/78">Aplicaciones web listas para crecer con tu negocio.</p>
                        </div>
                        <div class="flex items-start gap-3">
                            <CheckCircle2 class="mt-1 h-5 w-5 shrink-0 text-[#8ae4b8]" />
                            <p class="text-white/78">Integraciones entre herramientas, APIs y bases de datos.</p>
                        </div>
                        <div class="flex items-start gap-3">
                            <LockKeyhole class="mt-1 h-5 w-5 shrink-0 text-[#8ae4b8]" />
                            <p class="text-white/78">Buenas practicas de seguridad desde el diseno.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>
</template>
