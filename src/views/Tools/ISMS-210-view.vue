<script setup lang="ts">
import { PhotoIcon, UserCircleIcon } from '@heroicons/vue/24/solid'
import { ChevronDownIcon } from '@heroicons/vue/16/solid'
import { DocumentIcon } from '@heroicons/vue/24/outline'
import { XCircleIcon } from '@heroicons/vue/24/outline'
import { PlusCircleIcon } from '@heroicons/vue/24/outline'
import { MinusCircleIcon } from '@heroicons/vue/24/outline'

import { reactive, ref, watch } from 'vue'
import moment from 'moment'

const jirano = ref('')
const username = ref('')
const date = ref(moment().format('yyyy-MM-DD'))
const function_test = ref('')
const purpose = ref('')
const description = ref('')
const changeItemName = ref('Program')
const changes = reactive([{ name: '', desc: '' }])

watch(changes, (value) => {
  console.log(value)
})

watch(function_test, (value, old) => {
  if (purpose.value == old) {
    purpose.value = value
  }
  if (description.value == old) {
    description.value = value
  }
})

watch(purpose, (value, old) => {
  if (description.value == old) {
    description.value = value
  }
})

const NFR_urls = ref(new Map<string, string>())
const code_diff_urls = ref(new Map<string, string>())

const selectFile = (urls: Map<String, String>, event: Event) => {
  const target = event.target as HTMLInputElement
  if (target.files) {
    for (let i = 0; i < target.files.length; i++) {
      const f = target.files[i]
      const url = URL.createObjectURL(f)
      urls.set(f.name, url) // add new file
    }
  }
  target.value = '' // reset file change
}
</script>

<template>
  <div class="mx-auto max-w-2xl px-4 py-24 sm:px-6 sm:py-24 lg:px-8 bg-white">
    <form>
      <div class="space-y-12">
        <div class="border-b border-gray-900/10 pb-12">
          <h2 class="text-base/7 font-semibold text-gray-900">ISMS-210</h2>
          <p class="mt-1 text-sm/6 text-gray-600">
            You will create ISMS-210-P416, ISMS-210-P417, ISMS-210-P418, ISMS-210-P419 docx.
          </p>

          <div class="mt-10 grid grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-6">
            <div class="sm:col-span-4">
              <label for="jirano" class="block text-sm/6 font-medium text-gray-900">Jirano</label>
              <div class="mt-2">
                <div
                  class="flex items-center rounded-md bg-white pl-3 outline-1 outline -outline-offset-1 outline-gray-300 focus-within:outline-2 focus-within:-outline-offset-2 focus-within:outline-indigo-600"
                >
                  <input
                    type="text"
                    name="jirano"
                    id="jirano"
                    class="block min-w-0 grow py-1.5 pr-3 pl-1 text-base text-gray-900 placeholder:text-gray-400 focus:outline-none sm:text-sm/6"
                    placeholder="jirano"
                    v-model="jirano"
                  />
                </div>
              </div>
            </div>
            <div class="sm:col-span-4">
              <label for="username" class="block text-sm/6 font-medium text-gray-900"
                >UserName</label
              >
              <div class="mt-2">
                <div
                  class="flex items-center rounded-md bg-white pl-3 outline-1 outline -outline-offset-1 outline-gray-300 focus-within:outline-2 focus-within:-outline-offset-2 focus-within:outline-indigo-600"
                >
                  <input
                    type="text"
                    name="username"
                    id="username"
                    class="block min-w-0 grow py-1.5 pr-3 pl-1 text-base text-gray-900 placeholder:text-gray-400 focus:outline-none sm:text-sm/6"
                    placeholder="pyu"
                    v-model="username"
                  />
                </div>
              </div>
            </div>
            <div class="sm:col-span-4">
              <label for="date" class="block text-sm/6 font-medium text-gray-900">Date</label>
              <div class="mt-2">
                <div
                  class="flex items-center rounded-md bg-white pl-3 outline-1 outline -outline-offset-1 outline-gray-300 focus-within:outline-2 focus-within:-outline-offset-2 focus-within:outline-indigo-600"
                >
                  <input
                    type="date"
                    name="date"
                    id="date"
                    class="block min-w-0 grow py-1.5 pr-3 pl-1 text-base text-gray-900 placeholder:text-gray-400 focus:outline-none sm:text-sm/6"
                    v-model="date"
                  />
                </div>
              </div>
            </div>

            <div class="col-span-full">
              <label for="function-test" class="block text-sm/6 font-medium text-gray-900"
                >Function test</label
              >
              <div class="mt-2">
                <textarea
                  name="function-test"
                  id="function-test"
                  rows="3"
                  v-model="function_test"
                  class="block w-full resize-none rounded-md bg-white px-3 py-1.5 text-base text-gray-900 outline-1 outline -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
                />
              </div>
              <p class="mt-3 text-sm/6 text-gray-600">Write a few sentences about function test.</p>
            </div>
            <div class="col-span-full">
              <label for="purpose" class="block text-sm/6 font-medium text-gray-900">Purpose</label>
              <div class="mt-2">
                <textarea
                  name="purpose"
                  id="purpose"
                  rows="3"
                  v-model="purpose"
                  class="block w-full resize-none rounded-md bg-white px-3 py-1.5 text-base text-gray-900 outline-1 outline -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
                />
              </div>
              <!-- <p class="mt-3 text-sm/6 text-gray-600">Write a few sentences about function test.</p> -->
            </div>
            <div class="col-span-full">
              <label for="description" class="block text-sm/6 font-medium text-gray-900"
                >Description</label
              >
              <div class="mt-2">
                <textarea
                  name="description"
                  id="description"
                  rows="3"
                  v-model="description"
                  class="block w-full resize-none rounded-md bg-white px-3 py-1.5 text-base text-gray-900 outline-1 outline -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
                />
              </div>
              <!-- <p class="mt-3 text-sm/6 text-gray-600">Write a few sentences about function test.</p> -->
            </div>

            <div class="col-span-full">
              <label for="NFR-file-upload" class="block text-sm/6 font-medium text-gray-900"
                >NFR</label
              >
              <div
                class="mt-2 flex justify-center rounded-lg border border-dashed border-gray-900/25 py-10 flex-wrap"
              >
                <div class="mx-4 w-full flex overflow-x-scroll scroll-pre">
                  <TransitionGroup name="fade">
                    <div v-if="NFR_urls.size === 0" class="py-0 px-3 first:pl-6 last:pr-6 mx-auto">
                      <div class="flex flex-col items-center justify-center gap-3">
                        <div class="">
                          <PhotoIcon class="size-12 text-gray-300" aria-hidden="true" />
                        </div>
                        <strong
                          class="text-slate-900 w-12 h-4 truncate text-xs font-medium dark:text-slate-200"
                        >
                          &ensp;
                        </strong>
                      </div>
                    </div>
                    <template v-for="[key, value] of NFR_urls" :key="key">
                      <div class="py-0 px-3 first:pl-6 last:pr-6">
                        <div class="flex flex-col items-center justify-center gap-3">
                          <div class="relative">
                            <div class="absolute hover:backdrop-blur-sm size-12 group grid">
                              <XCircleIcon
                                @click="NFR_urls.delete(key)"
                                class="place-self-center size-8 ease-in-out text-red-500 scale-0 group-hover:scale-100 origin-center duration-300 cursor-pointer"
                              />
                            </div>
                            <img
                              v-if="key.endsWith('.webp')"
                              class="size-12 text-gray-300 border border-gray-3 rounded"
                              :alt="key"
                              :src="value"
                              aria-hidden="true"
                            />
                            <DocumentIcon v-else class="size-12 text-gray-300" aria-hidden="true" />
                          </div>
                          <strong
                            class="text-slate-900 w-12 h-4 truncate text-xs font-medium dark:text-slate-200"
                          >
                            {{ key }}
                          </strong>
                        </div>
                      </div>
                    </template>
                  </TransitionGroup>
                </div>

                <div class="text-center">
                  <div class="mt-2 flex text-sm/6 text-gray-600">
                    <label
                      for="NFR-file-upload"
                      class="relative cursor-pointer rounded-md bg-white font-semibold text-indigo-600 focus-within:ring-2 focus-within:ring-indigo-600 focus-within:ring-offset-2 focus-within:outline-hidden hover:text-indigo-500"
                    >
                      <span>Upload a file</span>
                      <input
                        id="NFR-file-upload"
                        name="NFR-file-upload"
                        @change="selectFile(NFR_urls, $event)"
                        type="file"
                        class="sr-only"
                        multiple
                      />
                    </label>
                    <p class="pl-1">or drag and drop</p>
                  </div>
                  <p class="text-xs/5 text-gray-600">PNG, JPG, GIF up to 10MB</p>
                </div>
              </div>
            </div>

            <div class="col-span-full">
              <label for="code-diff-file-upload" class="block text-sm/6 font-medium text-gray-900"
                >Code diff</label
              >
              <div
                class="mt-2 flex justify-center rounded-lg border border-dashed border-gray-900/25 py-10 flex-wrap"
              >
                <div class="mx-4 w-full flex overflow-x-scroll scroll-pre">
                  <TransitionGroup name="fade">
                    <div
                      v-if="code_diff_urls.size === 0"
                      class="py-0 px-3 first:pl-6 last:pr-6 mx-auto"
                    >
                      <div class="flex flex-col items-center justify-center gap-3">
                        <div class="">
                          <PhotoIcon class="size-12 text-gray-300" aria-hidden="true" />
                        </div>
                        <strong
                          class="text-slate-900 w-12 h-4 truncate text-xs font-medium dark:text-slate-200"
                        >
                          &ensp;
                        </strong>
                      </div>
                    </div>

                    <template v-for="[key, value] of code_diff_urls" :key="key">
                      <div class="py-0 px-3 first:pl-6 last:pr-6">
                        <div class="flex flex-col items-center justify-center gap-3">
                          <div class="relative">
                            <div
                              class="absolute hover:backdrop-blur-sm size-12 group grid"
                              @click="code_diff_urls.delete(key)"
                            >
                              <XCircleIcon
                                class="place-self-center ease-in-out size-8 text-red-500 scale-0 group-hover:scale-100 origin-center duration-300 cursor-pointer"
                              />
                            </div>
                            <img
                              v-if="key.endsWith('.webp')"
                              class="size-12 text-gray-300 border border-gray-3 rounded"
                              :alt="key"
                              :src="value"
                              aria-hidden="true"
                            />
                            <DocumentIcon v-else class="size-12 text-gray-300" aria-hidden="true" />
                          </div>
                          <strong
                            class="text-slate-900 w-12 h-4 truncate text-xs font-medium dark:text-slate-200"
                          >
                            {{ key }}
                          </strong>
                        </div>
                      </div>
                    </template>
                  </TransitionGroup>
                </div>

                <div class="text-center">
                  <div class="mt-2 flex text-sm/6 text-gray-600">
                    <label
                      for="code-diff-file-upload"
                      class="relative cursor-pointer rounded-md bg-white font-semibold text-indigo-600 focus-within:ring-2 focus-within:ring-indigo-600 focus-within:ring-offset-2 focus-within:outline-hidden hover:text-indigo-500"
                    >
                      <span>Upload a file</span>
                      <input
                        id="code-diff-file-upload"
                        name="code-diff-file-upload"
                        @change="selectFile(code_diff_urls, $event)"
                        type="file"
                        class="sr-only"
                        multiple
                      />
                    </label>
                    <p class="pl-1">or drag and drop</p>
                  </div>
                  <p class="text-xs/5 text-gray-600">PNG, JPG, GIF up to 10MB</p>
                </div>
              </div>
            </div>
            <fieldset class="sm:col-span-full">
              <legend class="block text-sm/6 font-medium text-gray-900">Changes</legend>
              <!-- <p class="mt-1 text-sm/6 text-gray-600">
                These are delivered via SMS to your mobile phone.
              </p> -->
              <div
                class="mt-6 sm:col-span-full border rounded-lg border-gray-300 bg-slate-50 p-4 space-y-4"
              >
                <div class="space-x-6 flex">
                  <div class="flex items-center gap-x-3">
                    <input
                      id="changes-program"
                      name="changes"
                      type="radio"
                      v-model="changeItemName"
                      value="Program"
                      checked
                      class="relative size-4 appearance-none rounded-full border border-gray-300 bg-white before:absolute before:inset-1 before:rounded-full before:bg-white not-checked:before:hidden checked:border-indigo-600 checked:bg-indigo-600 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:border-gray-300 disabled:bg-gray-100 disabled:before:bg-gray-400 forced-colors:appearance-auto forced-colors:before:hidden"
                    />
                    <label for="changes-program" class="block text-sm/6 font-medium text-gray-900"
                      >Program</label
                    >
                  </div>
                  <div class="flex items-center gap-x-3">
                    <input
                      id="changes-file-table"
                      name="changes"
                      type="radio"
                      v-model="changeItemName"
                      value="File/Table"
                      class="relative size-4 appearance-none rounded-full border border-gray-300 bg-white before:absolute before:inset-1 before:rounded-full before:bg-white not-checked:before:hidden checked:border-indigo-600 checked:bg-indigo-600 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:border-gray-300 disabled:bg-gray-100 disabled:before:bg-gray-400 forced-colors:appearance-auto forced-colors:before:hidden"
                    />
                    <label
                      for="changes-file-table"
                      class="block text-sm/6 font-medium text-gray-900"
                      >File / Table</label
                    >
                  </div>
                  <div class="flex items-center gap-x-3">
                    <input
                      id="changes-report"
                      name="changes"
                      type="radio"
                      v-model="changeItemName"
                      value="Report"
                      class="relative size-4 appearance-none rounded-full border border-gray-300 bg-white before:absolute before:inset-1 before:rounded-full before:bg-white not-checked:before:hidden checked:border-indigo-600 checked:bg-indigo-600 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:border-gray-300 disabled:bg-gray-100 disabled:before:bg-gray-400 forced-colors:appearance-auto forced-colors:before:hidden"
                    />
                    <label for="changes-report" class="block text-sm/6 font-medium text-gray-900"
                      >Report</label
                    >
                  </div>
                </div>
                <div class="mx-auto border rounded-lg shadow-sm">
                  <div class="mt-2">
                    <table class="border-collapse w-full text-sm">
                      <thead>
                        <tr class="">
                          <td class="border-b font-medium py-2 px-4 text-slate-400 text-left">
                            Num
                          </td>
                          <td class="border-b font-medium py-2 px-4 text-slate-400 text-left">
                            {{ changeItemName }} Name
                          </td>
                          <td class="border-b font-medium py-2 px-4 text-slate-400 text-left">
                            Description
                          </td>
                        </tr>
                      </thead>
                      <tbody class="bg-white">
                        <TransitionGroup name="fade">
                          <template v-for="n in changes.length" :key="n">
                            <tr class="border-b border-slate-100 last:border-slate-200">
                              <td
                                class="relative group font-medium py-2 px-4 text-slate-400 text-left focus-within:rounded focus-within:outline focus-within:outline-2 focus-within:-outline-offset-2 focus-within:outline-indigo-600"
                              >
                                <span class="group-hover:opacity-0 duration-300">
                                  {{ n }}
                                </span>
                                <div
                                  class="absolute grid top-0 left-0 grid-rows-2 grid-cols-2 scale-0 group-hover:scale-100 origin-center duration-300"
                                >
                                  <div class="row-span-1 cursor-pointer bg-indigo-200"></div>
                                  <div class="row-span-2 cursor-pointer bg-red-200">nihao</div>
                                  <div class="row-span-1 cursor-pointer bg-indigo-200">nihao</div>
                                </div>
                              </td>
                              <td
                                class="font-medium py-2 px-4 text-slate-400 text-left focus-within:rounded focus-within:outline focus-within:outline-2 focus-within:-outline-offset-2 focus-within:outline-indigo-600"
                              >
                                <input
                                  :id="'t_c_1_r' + n"
                                  type="text"
                                  class="w-full outline-none placeholder:italic placeholder:text-slate-300"
                                  v-model="changes[n - 1].name"
                                  placeholder="Write Something..."
                                />
                              </td>
                              <td
                                class="font-medium py-2 px-4 text-slate-400 text-left focus-within:rounded focus-within:outline focus-within:outline-2 focus-within:-outline-offset-2 focus-within:outline-indigo-600"
                              >
                                <input
                                  :id="'t_c_2_r' + n"
                                  type="text"
                                  class="w-full outline-none text-slate-400 placeholder:italic placeholder:text-slate-300"
                                  v-model="changes[n - 1].desc"
                                  placeholder="Write Something..."
                                />
                              </td>
                            </tr>
                          </template>
                        </TransitionGroup>
                      </tbody>
                    </table>
                    <div class="py-2">
                      <PlusCircleIcon
                        @click="changes.push({ name: '', desc: '' })"
                        class="mx-auto size-6 text-gray-300 hover:text-indigo-500 duration-300 cursor-pointer"
                      />
                    </div>
                  </div>
                </div>
              </div>
            </fieldset>
          </div>
        </div>

        <div class="border-b border-gray-900/10 pb-12">
          <h2 class="text-base/7 font-semibold text-gray-900">Personal Information</h2>
          <p class="mt-1 text-sm/6 text-gray-600">
            Use a permanent address where you can receive mail.
          </p>

          <div class="mt-10 grid grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-6">
            <div class="sm:col-span-3">
              <label for="first-name" class="block text-sm/6 font-medium text-gray-900"
                >First name</label
              >
              <div class="mt-2">
                <input
                  type="text"
                  name="first-name"
                  id="first-name"
                  autocomplete="given-name"
                  class="block w-full rounded-md bg-white px-3 py-1.5 text-base text-gray-900 outline-1 outline -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
                />
              </div>
            </div>

            <div class="sm:col-span-3">
              <label for="last-name" class="block text-sm/6 font-medium text-gray-900"
                >Last name</label
              >
              <div class="mt-2">
                <input
                  type="text"
                  name="last-name"
                  id="last-name"
                  autocomplete="family-name"
                  class="block w-full rounded-md bg-white px-3 py-1.5 text-base text-gray-900 outline-1 outline -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
                />
              </div>
            </div>

            <div class="sm:col-span-4">
              <label for="email" class="block text-sm/6 font-medium text-gray-900"
                >Email address</label
              >
              <div class="mt-2">
                <input
                  id="email"
                  name="email"
                  type="email"
                  autocomplete="email"
                  class="block w-full rounded-md bg-white px-3 py-1.5 text-base text-gray-900 outline-1 outline -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
                />
              </div>
            </div>

            <div class="sm:col-span-3">
              <label for="country" class="block text-sm/6 font-medium text-gray-900">Country</label>
              <div class="mt-2 grid grid-cols-1">
                <select
                  id="country"
                  name="country"
                  autocomplete="country-name"
                  class="col-start-1 row-start-1 w-full appearance-none rounded-md bg-white py-1.5 pr-8 pl-3 text-base text-gray-900 outline-1 outline -outline-offset-1 outline-gray-300 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
                >
                  <option>United States</option>
                  <option>Canada</option>
                  <option>Mexico</option>
                </select>
                <ChevronDownIcon
                  class="pointer-events-none col-start-1 row-start-1 mr-2 size-5 self-center justify-self-end text-gray-500 sm:size-4"
                  aria-hidden="true"
                />
              </div>
            </div>

            <div class="col-span-full">
              <label for="street-address" class="block text-sm/6 font-medium text-gray-900"
                >Street address</label
              >
              <div class="mt-2">
                <input
                  type="text"
                  name="street-address"
                  id="street-address"
                  autocomplete="street-address"
                  class="block w-full rounded-md bg-white px-3 py-1.5 text-base text-gray-900 outline-1 outline -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
                />
              </div>
            </div>

            <div class="sm:col-span-2 sm:col-start-1">
              <label for="city" class="block text-sm/6 font-medium text-gray-900">City</label>
              <div class="mt-2">
                <input
                  type="text"
                  name="city"
                  id="city"
                  autocomplete="address-level2"
                  class="block w-full rounded-md bg-white px-3 py-1.5 text-base text-gray-900 outline-1 outline -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
                />
              </div>
            </div>

            <div class="sm:col-span-2">
              <label for="region" class="block text-sm/6 font-medium text-gray-900"
                >State / Province</label
              >
              <div class="mt-2">
                <input
                  type="text"
                  name="region"
                  id="region"
                  autocomplete="address-level1"
                  class="block w-full rounded-md bg-white px-3 py-1.5 text-base text-gray-900 outline-1 outline -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
                />
              </div>
            </div>

            <div class="sm:col-span-2">
              <label for="postal-code" class="block text-sm/6 font-medium text-gray-900"
                >ZIP / Postal code</label
              >
              <div class="mt-2">
                <input
                  type="text"
                  name="postal-code"
                  id="postal-code"
                  autocomplete="postal-code"
                  class="block w-full rounded-md bg-white px-3 py-1.5 text-base text-gray-900 outline-1 outline -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
                />
              </div>
            </div>
          </div>
        </div>

        <div class="border-b border-gray-900/10 pb-12">
          <h2 class="text-base/7 font-semibold text-gray-900">Notifications</h2>
          <p class="mt-1 text-sm/6 text-gray-600">
            We'll always let you know about important changes, but you pick what else you want to
            hear about.
          </p>

          <div class="mt-10 space-y-10">
            <fieldset>
              <legend class="text-sm/6 font-semibold text-gray-900">By email</legend>
              <div class="mt-6 space-y-6">
                <div class="flex gap-3">
                  <div class="flex h-6 shrink-0 items-center">
                    <div class="group grid size-4 grid-cols-1">
                      <input
                        id="comments"
                        aria-describedby="comments-description"
                        name="comments"
                        type="checkbox"
                        checked
                        class="col-start-1 row-start-1 appearance-none rounded-sm border border-gray-300 bg-white checked:border-indigo-600 checked:bg-indigo-600 indeterminate:border-indigo-600 indeterminate:bg-indigo-600 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:border-gray-300 disabled:bg-gray-100 disabled:checked:bg-gray-100 forced-colors:appearance-auto"
                      />
                      <svg
                        class="pointer-events-none col-start-1 row-start-1 size-3.5 self-center justify-self-center stroke-white group-has-disabled:stroke-gray-950/25"
                        viewBox="0 0 14 14"
                        fill="none"
                      >
                        <path
                          class="opacity-0 group-has-checked:opacity-100"
                          d="M3 8L6 11L11 3.5"
                          stroke-width="2"
                          stroke-linecap="round"
                          stroke-linejoin="round"
                        />
                        <path
                          class="opacity-0 group-has-indeterminate:opacity-100"
                          d="M3 7H11"
                          stroke-width="2"
                          stroke-linecap="round"
                          stroke-linejoin="round"
                        />
                      </svg>
                    </div>
                  </div>
                  <div class="text-sm/6">
                    <label for="comments" class="font-medium text-gray-900">Comments</label>
                    <p id="comments-description" class="text-gray-500">
                      Get notified when someones posts a comment on a posting.
                    </p>
                  </div>
                </div>
                <div class="flex gap-3">
                  <div class="flex h-6 shrink-0 items-center">
                    <div class="group grid size-4 grid-cols-1">
                      <input
                        id="candidates"
                        aria-describedby="candidates-description"
                        name="candidates"
                        type="checkbox"
                        class="col-start-1 row-start-1 appearance-none rounded-sm border border-gray-300 bg-white checked:border-indigo-600 checked:bg-indigo-600 indeterminate:border-indigo-600 indeterminate:bg-indigo-600 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:border-gray-300 disabled:bg-gray-100 disabled:checked:bg-gray-100 forced-colors:appearance-auto"
                      />
                      <svg
                        class="pointer-events-none col-start-1 row-start-1 size-3.5 self-center justify-self-center stroke-white group-has-disabled:stroke-gray-950/25"
                        viewBox="0 0 14 14"
                        fill="none"
                      >
                        <path
                          class="opacity-0 group-has-checked:opacity-100"
                          d="M3 8L6 11L11 3.5"
                          stroke-width="2"
                          stroke-linecap="round"
                          stroke-linejoin="round"
                        />
                        <path
                          class="opacity-0 group-has-indeterminate:opacity-100"
                          d="M3 7H11"
                          stroke-width="2"
                          stroke-linecap="round"
                          stroke-linejoin="round"
                        />
                      </svg>
                    </div>
                  </div>
                  <div class="text-sm/6">
                    <label for="candidates" class="font-medium text-gray-900">Candidates</label>
                    <p id="candidates-description" class="text-gray-500">
                      Get notified when a candidate applies for a job.
                    </p>
                  </div>
                </div>
                <div class="flex gap-3">
                  <div class="flex h-6 shrink-0 items-center">
                    <div class="group grid size-4 grid-cols-1">
                      <input
                        id="offers"
                        aria-describedby="offers-description"
                        name="offers"
                        type="checkbox"
                        class="col-start-1 row-start-1 appearance-none rounded-sm border border-gray-300 bg-white checked:border-indigo-600 checked:bg-indigo-600 indeterminate:border-indigo-600 indeterminate:bg-indigo-600 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:border-gray-300 disabled:bg-gray-100 disabled:checked:bg-gray-100 forced-colors:appearance-auto"
                      />
                      <svg
                        class="pointer-events-none col-start-1 row-start-1 size-3.5 self-center justify-self-center stroke-white group-has-disabled:stroke-gray-950/25"
                        viewBox="0 0 14 14"
                        fill="none"
                      >
                        <path
                          class="opacity-0 group-has-checked:opacity-100"
                          d="M3 8L6 11L11 3.5"
                          stroke-width="2"
                          stroke-linecap="round"
                          stroke-linejoin="round"
                        />
                        <path
                          class="opacity-0 group-has-indeterminate:opacity-100"
                          d="M3 7H11"
                          stroke-width="2"
                          stroke-linecap="round"
                          stroke-linejoin="round"
                        />
                      </svg>
                    </div>
                  </div>
                  <div class="text-sm/6">
                    <label for="offers" class="font-medium text-gray-900">Offers</label>
                    <p id="offers-description" class="text-gray-500">
                      Get notified when a candidate accepts or rejects an offer.
                    </p>
                  </div>
                </div>
              </div>
            </fieldset>

            <fieldset>
              <legend class="text-sm/6 font-semibold text-gray-900">Push notifications</legend>
              <p class="mt-1 text-sm/6 text-gray-600">
                These are delivered via SMS to your mobile phone.
              </p>
              <div class="mt-6 space-y-6">
                <div class="flex items-center gap-x-3">
                  <input
                    id="push-everything"
                    name="push-notifications"
                    type="radio"
                    checked
                    class="relative size-4 appearance-none rounded-full border border-gray-300 bg-white before:absolute before:inset-1 before:rounded-full before:bg-white not-checked:before:hidden checked:border-indigo-600 checked:bg-indigo-600 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:border-gray-300 disabled:bg-gray-100 disabled:before:bg-gray-400 forced-colors:appearance-auto forced-colors:before:hidden"
                  />
                  <label for="push-everything" class="block text-sm/6 font-medium text-gray-900"
                    >Everything</label
                  >
                </div>
                <div class="flex items-center gap-x-3">
                  <input
                    id="push-email"
                    name="push-notifications"
                    type="radio"
                    class="relative size-4 appearance-none rounded-full border border-gray-300 bg-white before:absolute before:inset-1 before:rounded-full before:bg-white not-checked:before:hidden checked:border-indigo-600 checked:bg-indigo-600 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:border-gray-300 disabled:bg-gray-100 disabled:before:bg-gray-400 forced-colors:appearance-auto forced-colors:before:hidden"
                  />
                  <label for="push-email" class="block text-sm/6 font-medium text-gray-900"
                    >Same as email</label
                  >
                </div>
                <div class="flex items-center gap-x-3">
                  <input
                    id="push-nothing"
                    name="push-notifications"
                    type="radio"
                    class="relative size-4 appearance-none rounded-full border border-gray-300 bg-white before:absolute before:inset-1 before:rounded-full before:bg-white not-checked:before:hidden checked:border-indigo-600 checked:bg-indigo-600 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:border-gray-300 disabled:bg-gray-100 disabled:before:bg-gray-400 forced-colors:appearance-auto forced-colors:before:hidden"
                  />
                  <label for="push-nothing" class="block text-sm/6 font-medium text-gray-900"
                    >No push notifications</label
                  >
                </div>
              </div>
            </fieldset>
          </div>
        </div>
      </div>

      <div class="mt-6 flex items-center justify-end gap-x-6">
        <button type="button" class="text-sm/6 font-semibold text-gray-900">Cancel</button>
        <button
          type="submit"
          class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-xs hover:bg-indigo-500 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
        >
          Save
        </button>
      </div>
    </form>
  </div>
</template>

<style lang="css" scoped>
/* 1. 声明过渡效果 */
.fade-move,
.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s cubic-bezier(0.55, 0, 0.1, 1);
}

/* 2. 声明进入和离开的状态 */
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: scaleY(0.01) translate(30px, 0);
}

/* 3. 确保离开的项目被移除出了布局流
      以便正确地计算移动时的动画效果。 */
.fade-leave-active {
  position: absolute;
}
</style>
