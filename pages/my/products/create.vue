<template>
  <section class="bg-white dark:bg-gray-900">
    <div class="py-8 px-4 mx-auto">
      <h2 class="mb-4 text-xl font-bold text-gray-900 dark:text-white">
        Add a new event
      </h2>
      <VForm
        id="products_create"
        class="form"
        novalidate
        @submit="submitForm()"
        :validation-schema="form">
        <div
          class="gap-4 sm:grid sm:grid-cols-2 xl:grid-cols-3 sm:gap-6 sm:mb-2">
          <div class="mb-4 space-y-4 xl:col-span-2">
            <div class="flex flex-row gap-4">
              <div class="md:basis-1/2">
                <label for="title" class="custom-input-label">Title</label>
                <Field
                  type="text"
                  name="title"
                  class="custom-input"
                  v-model="model.title" />
                <div class="text-red-500 text-sm p-1">
                  <ErrorMessage name="title" />
                </div>
              </div>
              <div class="md:basis-1/2">
                <label for="title" class="custom-input-label">Type</label>
                <Field
                  as="select"
                  name="type"
                  class="custom-input"
                  v-model="model.type">
                  <option
                    :value="item.value"
                    v-for="(item, index) in types"
                    :key="index">
                    {{ item.name }}
                  </option>
                </Field>
                <div class="text-red-500 text-sm p-1">
                  <div class="fv-help-block">
                    <ErrorMessage name="type" />
                  </div>
                </div>
              </div>
            </div>
            <div>
              <label for="slogan" class="custom-input-label">Slogan</label>
              <Field
                type="text"
                name="slogan"
                class="custom-input"
                v-model="model.slogan" />
              <div class="text-red-500 text-sm p-1">
                <ErrorMessage name="slogan" />
              </div>
            </div>
            <div>
              <label for="description" class="custom-input-label"
                >Introduction</label
              >
              <Field
                type="text"
                name="introduction"
                class="custom-input"
                v-model="model.introduction" />
              <div class="text-red-500 text-sm p-1">
                <ErrorMessage name="introduction" />
              </div>
            </div>
            <div>
              <label for="description" class="custom-input-label"
                >Description</label
              >
              <Field
                type="text"
                name="description"
                class="custom-input"
                v-model="model.description" />
              <div class="text-red-500 text-sm p-1">
                <ErrorMessage name="description" />
              </div>
            </div>

            <div class="flex flex-row gap-4">
              <label class="custom-input-label"> Logo</label>
              <div class="flex basis-1/2 items-center justify-center">
                <label
                  class="flex flex-col items-center justify-center w-full h-32 border-2 border-gray-300 border-dashed rounded-lg cursor-pointer bg-gray-50 dark:hover:bg-bray-800 dark:bg-gray-700 hover:bg-gray-100 dark:border-gray-600 dark:hover:border-gray-500 dark:hover:bg-gray-600">
                  <div
                    class="flex flex-col items-center justify-center pt-5 pb-6">
                    <Icon
                      class="w-10 h-10 mb-3 text-gray-400 me-2"
                      name="mdi:cloud-upload-outline"
                      size="23px" />

                    <p class="mb-2 text-sm text-gray-500 dark:text-gray-400">
                      <span class="font-semibold">Click to upload</span> or drag
                      and drop
                    </p>
                    <p class="text-xs text-gray-500 dark:text-gray-400">
                      SVG, PNG, JPG or GIF (MAX. 5 MB)
                    </p>
                  </div>
                  <Field
                    name="logoImg"
                    type="file"
                    class="hidden"
                    @change="onFileChange($event)" />
                  <div class="text-red-500 text-sm p-1">
                    <ErrorMessage name="logoImg" />
                  </div>
                </label>
              </div>

              <label class="custom-input-label"> Cover</label>

              <div class="flex basis-1/2 items-center justify-center">
                <label
                  class="flex flex-col items-center justify-center w-full h-32 border-2 border-gray-300 border-dashed rounded-lg cursor-pointer bg-gray-50 dark:hover:bg-bray-800 dark:bg-gray-700 hover:bg-gray-100 dark:border-gray-600 dark:hover:border-gray-500 dark:hover:bg-gray-600">
                  <div
                    class="flex flex-col items-center justify-center pt-5 pb-6">
                    <Icon
                      class="w-10 h-10 mb-3 text-gray-400 me-2"
                      name="mdi:cloud-upload-outline"
                      size="23px" />
                    <p class="mb-2 text-sm text-gray-500 dark:text-gray-400">
                      <span class="font-semibold">Click to upload</span> or drag
                      and drop
                    </p>
                    <p class="text-xs text-gray-500 dark:text-gray-400">
                      SVG, PNG, JPG or GIF (MAX. 5 MB)
                    </p>
                  </div>
                  <Field
                    name="coverImg"
                    type="file"
                    class="hidden"
                    @change="onFileChange($event)" />
                  <div class="text-red-500 text-sm p-1">
                    <ErrorMessage name="coverImg" />
                  </div>
                </label>
              </div>
            </div>
            <div class="flex flex-row gap-4"></div>
          </div>
          <div class="mb-4 space-y-4">
            <div>
              <label for="add-guests" class="custom-input-label"
                >Add guests</label
              >
              <div class="relative">
                <input
                  type="text"
                  id="add-guests"
                  class="block p-3 pl-4 w-full text-sm text-gray-900 bg-gray-50 rounded border outline-none border-gray-300 focus:ring-primary-500 focus:border-primary-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500"
                  placeholder="Add guest email"
                  required />
                <button
                  type="button"
                  class="text-white absolute inline-flex items-center right-2.5 bottom-2.5 bg-primary-700 hover:bg-primary-800 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded text-xs px-3 py-1.5 dark:bg-primary-600 dark:hover:bg-primary-700 dark:focus:ring-primary-800">
                  <Icon name="mdi:plus" size="17px" class="me-2" />
                  Add
                </button>
              </div>
            </div>
            <div class="items-center md:flex md:space-x-4">
              <div class="flex flex-shrink-0 mb-4 -space-x-4 md:mb-0">
                <img
                  class="w-8 h-8 rounded-full border-2 border-white dark:border-gray-800"
                  src="https://flowbite.s3.amazonaws.com/blocks/marketing-ui/avatars/helene-engels.png"
                  alt="Helene Engels" />
                <img
                  class="w-8 h-8 rounded-full border-2 border-white dark:border-gray-800"
                  src="https://flowbite.s3.amazonaws.com/blocks/marketing-ui/avatars/robert-brown.png"
                  alt="Robert Brown" />
                <img
                  class="w-8 h-8 rounded-full border-2 border-white dark:border-gray-800"
                  src="https://flowbite.s3.amazonaws.com/blocks/marketing-ui/avatars/bonnie-green.png"
                  alt="Bonnie Green" />
                <a
                  class="flex justify-center items-center w-8 h-8 text-xs font-medium text-white bg-gray-700 rounded-full border-2 border-white hover:bg-gray-600 dark:border-gray-800"
                  href="#"
                  >+9</a
                >
              </div>
              <button
                type="button"
                class="inline-flex items-center py-2 px-3 text-xs font-medium text-gray-900 bg-white rounded border border-gray-200 focus:outline-none hover:bg-gray-100 hover:text-primary-700 focus:z-10 focus:ring-4 focus:ring-gray-100 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700">
                <Icon name="mdi:plus" size="15px" class="me-2" />
                Add member
              </button>
              <button
                type="button"
                class="inline-flex items-center py-2 px-3 ml-2 text-xs font-medium text-gray-900 bg-white rounded border border-gray-200 sm:ml-0 focus:outline-none hover:bg-gray-100 hover:text-primary-700 focus:z-10 focus:ring-4 focus:ring-gray-100 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700">
                <Icon name="mdi:clock-outline" size="16px" class="me-2" />
                Find a time
              </button>
            </div>
            <div>
              <label
                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                >Guest Permissions</label
              >
              <div class="space-y-3">
                <div class="flex items-center mr-4">
                  <input
                    id="guest-permission-1-checkbox"
                    type="checkbox"
                    value=""
                    name="guest-permission-checkbox"
                    class="w-4 h-4 bg-gray-100 rounded border-gray-300 text-primary-600 focus:ring-primary-500 dark:focus:ring-primary-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600" />
                  <label
                    for="guest-permission-1-checkbox"
                    class="ml-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                    >Modify event</label
                  >
                </div>
                <div class="flex items-center mr-4">
                  <input
                    id="guest-permission-2-checkbox"
                    type="checkbox"
                    value=""
                    name="guest-permission-checkbox"
                    class="w-4 h-4 bg-gray-100 rounded border-gray-300 text-primary-600 focus:ring-primary-500 dark:focus:ring-primary-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600" />
                  <label
                    for="guest-permission-2-checkbox"
                    class="ml-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                    >Invite others</label
                  >
                </div>
                <div class="flex items-center mr-4">
                  <input
                    checked
                    id="guest-permission-3-checkbox"
                    type="checkbox"
                    value=""
                    name="guest-permission-checkbox"
                    class="w-4 h-4 bg-gray-100 rounded border-gray-300 text-primary-600 focus:ring-primary-500 dark:focus:ring-primary-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600" />
                  <label
                    for="guest-permission-3-checkbox"
                    class="ml-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                    >See guest list</label
                  >
                </div>
              </div>
            </div>
          </div>
        </div>
        <button
          type="submit"
          class="text-white justify-center bg-primary-700 hover:bg-primary-800 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded text-sm px-5 py-2.5 text-center dark:bg-primary-600 dark:hover:bg-primary-700 dark:focus:ring-primary-800">
          Add new event
        </button>
      </VForm>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ErrorMessage, Field, Form as VForm } from "vee-validate";
import * as Yup from "yup";

const { fetchCategories, categories, fetchMarkets, markets, fetchPlatforms } =
  useProductStore();

const types = ref<Types[]>([
  {
    name: "BOT",
    value: 13000,
  },
  {
    name: "INDICATOR",
    value: 13001,
  },
  {
    name: "SYSTEM",
    value: 13002,
  },
  {
    name: "SCRIPT",
    value: 13003,
  },
  {
    name: "TEMPLATE",
    value: 13004,
  },
  {
    name: "ALGORITHM",
    value: 13005,
  },
  {
    name: "ARTIFICIAL_INTELLIGENCE",
    value: 13006,
  },
  {
    name: "PORTFOLIO",
    value: 13007,
  },
  {
    name: "AI_LIVE",
    value: 13008,
  },
  {
    name: "FUNDED_ACCOUNT",
    value: 13009,
  },
  {
    name: "TRADING_SIGNAL",
    value: 13010,
  },
  {
    name: "TRADING_STRATEGY",
    value: 13011,
  },
  {
    name: "COURSE",
    value: 13012,
  },
]);
const model = ref<Product>({} as Product);
// Validations Account Details
const form = Yup.object().shape({
  title: Yup.string().required().max(128).label("Title"),
  slogan: Yup.string().required().max(256).label("Slogan"),
  logo: Yup.mixed().nonNullable().label("Logo"),
  cover: Yup.mixed().nonNullable().label("Cover"),
  type: Yup.number().required().label("Type"),
  introduction: Yup.string().required().max(512).label("Introduction"),
  description: Yup.string().required().max(1024).label("Description"),
  categories: Yup.array().of(Yup.string()).required().label("Categories"),
  tags: Yup.array().of(Yup.string()).required().label("Tags"),
  platforms: Yup.array().of(Yup.string()).required().label("Platforms"),
  logoImg: Yup.mixed<FileList>() // Pass in the type of `fileUpload`
    .test("logoImg", "Only documents up to 5MB are permitted.", (files) => {
      !files || // Check if `files` is defined
        files.length === 0 || // Check if `files` is not an empty list
        Array.from(files).every((file) => file.size <= 5_000_000);
    })
    .required(),

  coverImg: Yup.mixed<FileList>() // Pass in the type of `fileUpload`
    .test("coverImg", "Only documents up to 5MB are permitted.", (files) => {
      !files || // Check if `files` is defined
        files.length === 0 || // Check if `files` is not an empty list
        Array.from(files).every((file) => file.size <= 5_000_000);
    })
    .required(),
});

onMounted(() => {
  nextTick(() => {
    fetchCategories();
    fetchMarkets();
    fetchPlatforms();
  });
});

const onFileChange = (e: any) => {
  var files = e.target.files || e.dataTransfer.files;
  if (!files.length) return;
  model.value.logo = files[0];
  console.log(e.target.files || e.dataTransfer.files);
};
const submitForm = async () => {
  console.log("submitForm", model.value);
};
</script>

<style scoped>
.custom-input-label {
  @apply block mb-2 text-sm font-medium text-gray-900 dark:text-white;
}
.custom-input {
  @apply bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded outline-none focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500;
}
</style>
