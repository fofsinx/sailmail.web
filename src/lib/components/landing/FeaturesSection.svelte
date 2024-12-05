<script lang="ts">
  import { Code, Users, Mail, FileText, Database, Activity, Webhook } from 'lucide-svelte';
  
  const features = [
    {
      icon: Mail,
      title: "Multi-Provider Support",
      description: "Deploy with your choice of SMTP providers. Switch between providers seamlessly."
    },
    {
      icon: Users,
      title: "Team Collaboration",
      description: "Built for teams from day one. Manage roles, permissions, and workspaces effortlessly."
    },
    {
      icon: FileText,
      title: "Template Magic",
      description: "Create stunning emails with our intuitive template editor. See changes in real-time."
    },
    {
      icon: Code,
      title: "REST APIs That Make Sense",
      description: "Well-documented, predictable REST APIs that speak developer language."
    },
    {
      icon: Activity,
      title: "Campaign Analytics",
      description: "Track opens, clicks, bounces, and conversions with comprehensive analytics."
    },
    {
      icon: Webhook,
      title: "Webhooks & Events",
      description: "Stay informed with real-time event notifications for seamless integration."
    }
  ];
</script>

<section class="py-24 bg-gradient-to-b from-background to-secondary/20">
  <div class="container px-4 md:px-6">
    <div class="flex flex-col items-center justify-center space-y-4 text-center">
      <div class="space-y-2">
        <h2 class="text-3xl font-bold tracking-tighter sm:text-5xl">
          Built for Modern Development Teams
        </h2>
        <p class="max-w-[900px] text-gray-500 md:text-xl/relaxed lg:text-base/relaxed xl:text-xl/relaxed dark:text-gray-400">
          Everything you need to manage and scale your email operations
        </p>
      </div>
    </div>
    <div class="mx-auto grid max-w-5xl grid-cols-1 gap-6 pt-12 md:grid-cols-2 lg:grid-cols-3">
      {#each features as feature}
        <div class="relative overflow-hidden rounded-lg border bg-background p-6">
          <div class="flex h-12 w-12 items-center justify-center rounded-lg bg-primary/10">
            <svelte:component this={feature.icon} class="size-6 text-primary" />
          </div>
          <div class="mt-4 space-y-2">
            <h3 class="font-bold">{feature.title}</h3>
            <p class="text-sm text-gray-500 dark:text-gray-400">
              {feature.description}
            </p>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section> 