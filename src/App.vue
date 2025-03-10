<script setup>
import { ref } from 'vue'
import { Button } from '@/components/ui/button'
import { Card, CardHeader, CardTitle, CardDescription, CardContent } from '@/components/ui/card'
import { Input } from '@/components/ui/input'
import { Avatar, AvatarImage, AvatarFallback } from '@/components/ui/avatar'

const projects = ref([
  { title: 'Super Cool Project', description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit...' },
  // Add other projects...
])

const announcements = ref([
  { title: 'Site Maintenance', content: 'System update scheduled for next week...' },
  // Add other announcements...
])

const trending = ref([
  { user: '@tegan', role: 'World Peace Builder' },
  // Add other trending items...
])
</script>

<template>
  <div class="min-h-screen bg-slate-800">
    <div class="flex">
      <!-- Sidebar -->
      <aside class="hidden md:flex md:w-64 flex-col fixed h-full bg-slate-900">
        <div class="p-4">
          <h1 class="text-3xl font-bold text-emerald-500">Sezer</h1>
        </div>
        
        <nav class="flex-1 px-2 py-4 space-y-2">
          <Button variant="ghost" class="w-full justify-start text-white hover:bg-slate-700">
            Home
          </Button>
          <!-- Repeat for other nav items -->
        </nav>
      </aside>

      <!-- Main Content -->
      <div class="flex-1 md:ml-64">
        <!-- Header -->
        <header class="bg-slate-800 border-b border-slate-700 p-4">
          <div class="flex items-center justify-between">
            <Button variant="ghost" size="icon" class="md:hidden text-white">
              <MenuIcon class="h-6 w-6" />
            </Button>

            <div class="flex-1 max-w-xl px-4">
              <Input type="search" placeholder="Search..." class="bg-slate-700 border-slate-600 text-white" />
            </div>

            <div class="flex items-center gap-4">
              <Avatar>
                <AvatarImage src="https://avatars.githubusercontent.com/u/157473087?v=4" />
                <AvatarFallback>AK</AvatarFallback>
              </Avatar>
              <span class="hidden md:block text-white font-medium">Ahmed Khalid</span>
            </div>
          </div>

          <div class="mt-6 flex flex-col md:flex-row md:items-center md:justify-between">
            <div class="flex items-center gap-4">
              <Avatar class="h-12 w-12">
                <AvatarImage src="https://avatars.githubusercontent.com/u/157473087?v=4" />
                <AvatarFallback>AK</AvatarFallback>
              </Avatar>
              <h2 class="text-2xl font-bold text-white">Welcome Ahmed, <span class="text-emerald-500">John</span></h2>
            </div>
            <div class="mt-4 md:mt-0 flex gap-2">
              <Button variant="default">New Project</Button>
              <Button variant="default">Upload</Button>
              <Button variant="default">Share</Button>
            </div>
          </div>
        </header>

        <!-- Main Area -->
        <main class="p-6">
          <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
            <!-- Projects -->
            <div class="lg:col-span-2 space-y-4">
              <h3 class="text-xl font-bold text-white">Your Projects</h3>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <Card v-for="(project, index) in projects" :key="index" class="bg-slate-700 border-slate-600">
                  <CardHeader>
                    <CardTitle class="text-white">{{ project.title }}</CardTitle>
                    <CardDescription class="text-slate-300">
                      {{ project.description }}
                    </CardDescription>
                  </CardHeader>
                </Card>
              </div>
            </div>

            <!-- Right Sidebar -->
            <div class="space-y-6">
              <!-- Announcements -->
              <div class="space-y-4">
                <h3 class="text-xl font-bold text-white">Announcements</h3>
                <Card class="bg-slate-700 border-slate-600">
                  <CardContent class="p-4 space-y-4">
                    <div v-for="(announcement, index) in announcements" :key="index" class="border-b border-slate-600 pb-4 last:border-0">
                      <h4 class="font-semibold text-white">{{ announcement.title }}</h4>
                      <p class="text-sm text-slate-300">{{ announcement.content }}</p>
                    </div>
                  </CardContent>
                </Card>
              </div>

              <!-- Trending -->
              <div class="space-y-4">
                <h3 class="text-xl font-bold text-white">Trending</h3>
                <Card class="bg-slate-700 border-slate-600">
                  <CardContent class="p-4 space-y-4">
                    <div v-for="(item, index) in trending" :key="index" class="flex items-center gap-4">
                      <Avatar>
                        <AvatarImage src="https://avatars.githubusercontent.com/u/157473087?v=4" />
                        <AvatarFallback>AK</AvatarFallback>
                      </Avatar>
                      <div>
                        <h4 class="font-medium text-white">{{ item.user }}</h4>
                        <p class="text-sm text-slate-300">{{ item.role }}</p>
                      </div>
                    </div>
                  </CardContent>
                </Card>
              </div>
            </div>
          </div>
        </main>
      </div>
    </div>
  </div>
</template>