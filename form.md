###### [Home](/_doc)

## \# **OCForm**

- ### **Usage**

  \- Use the Form component to validate form data using schema libraries Zod.

  \- It works with the FormGroup component to display error messages around form elements automatically.

  \- The form component requires two props:

  \+ state - a reactive object holding the form's state.

  \+ schema - a schema object from Zod.

```vue
<template>
  <OCForm :schema="schema" :state="state" class="space-y-4" @submit="onSubmit">
    <OCFormGroup label="Email" name="email">
      <OCInput v-model="state.email" placeholder="Please enter email" />
    </OCFormGroup>

    <OCFormGroup label="Password" name="password">
      <OCInput
        v-model="state.password"
        type="password"
        placeholder="Please enter password"
      />
    </OCFormGroup>

    <UButton type="submit"> Submit </UButton>
  </OCForm>
</template>

<script setup>
import { z } from "zod";

const schema = z.object({
  email: z.string().email("Invalid email"),
  password: z.string().min(8, "Must be at least 8 characters"),
});

const state = ref({
  email: undefined,
  password: undefined,
});

async function onSubmit(event) {
  console.log(event.data);
}
</script>
```

- ### **Input events**

  \- The Form component automatically triggers validation upon submit, input, blur or change events.

```vue
<template>
  <OCForm
    ref="form"
    id="form"
    :schema="schema"
    :state="state"
    class="space-y-4"
    @on-submit="onSubmit"
  >
    <OCFormGroup required label="OCInput" name="input">
      <OCInput v-model="state.input" placeholder="Please enter input" />
    </OCFormGroup>

    <OCFormGroup label="OCRadioGroup" name="radio" required>
      <OCRadios
        v-model="state.radio"
        :options="[
          { value: 1, label: 'Option 1' },
          { value: 2, label: 'Option 2' },
        ]"
      >
      </OCRadios>
    </OCFormGroup>

    <OCFormGroup label="OCCheckbox" name="checkbox" required>
      <OCCheckboxes
        v-model="state.checkbox"
        :options="[
          { value: 'first', label: 'First' },
          { value: 'second', label: 'Second' },
        ]"
      />
    </OCFormGroup>

    <OCFormGroup required label="OCSelect">
      <OCSelect
        v-model="state.select"
        ref="selector"
        error-message="Not good for leaving empty"
        pk="Id"
        text="Name"
        :options="{
          placeholder: 'Please select item',
        }"
        :api="{
          url: '/api/student/GetListStudent',
          method: 'post',
        }"
      />
    </OCFormGroup>

    <OCFormGroup label="OCTextarea" name="textarea" required>
      <OCTextarea
        v-model="state.textarea"
        :auto-resize="true"
        placeholder="textarea"
        :max-rows="6"
      />
    </OCFormGroup>
  </OCForm>
</template>

<script setup>
import { z } from "zod";

const schema = z.object({
  input: z.string({ required_error: "Input is required" }),
  radio: z.number({ required_error: "Radio is required" }),
  checkbox: z.string().array().min(1, "Checkbox is required"),
  select: z.any().refine((val) => validateSelect("#form")),
  textarea: z
    .string({ required_error: "Textarea is required" })
    .min(1, "Textarea is required"),
});

const state = ref({
  input: undefined,
  radio: undefined,
  checkbox: [],
  select: undefined,
  textarea: undefined,
});

async function onSubmit(event) {
  console.log(event.data);
}
</script>
```

- ### Validate Check with Server

```vue
<template>
  <OCForm
    :schema="schema"
    :state="state"
    class="space-y-4"
    @on-submit="onSubmit"
  >
    <OCFormGroup required label="Code" name="code">
      <OCInput v-model="state.code" placeholder="Please enter code" />
    </OCFormGroup>

    <OCFormGroup required label="Name" name="name">
      <OCInput v-model="state.name" placeholder="Please enter input" />
    </OCFormGroup>
  </OCForm>
</template>

<script setup>
import { z } from "zod";

const schema = z.object({
  code: z
    .string({ required_error: "Code is required" })
    .min(1, "Code is required")
    .refine(async (d) => {
      const { data, error } = await useHttp("/api/enrollment/get", {
        method: "post",
        data: { Search: d },
      });
      const result = data.value
        ?.filter((e) => e.EnrollCourseCode)
        ?.map((e) => e.EnrollCourseCode.trim().toLowerCase());

      if (error.value) return false;

      return !result.includes(d.trim().toLowerCase());
    }, "Code already exists"),
  name: z.string({ required_error: "Name is required" }),
});

const state = ref({
  code: undefined,
  name: undefined,
});

async function onSubmit(event) {
  console.log(event.data);
}
</script>
```

- ### ref of OCForm

  \- **ref** have **submit()**, **clearValidate()** and object **ocForm**.

```vue
<template>
  <OCForm
    ref="ocForm"
    :schema="schema"
    :state="state"
    class="space-y-4"
    @on-submit="onSubmit"
  >
    <OCFormGroup required label="Input" name="input">
      <OCInput v-model="state.input" placeholder="Please enter input" />
    </OCFormGroup>
  </OCForm>
</template>

<script setup>
import { z } from "zod";

const ocForm = ref();

const schema = z.object({
  input: z.string({ required_error: "Input is required" }),
});

const state = ref({
  input: undefined,
});

mounted(() => {
  console.log("ocForm", ocForm.value);
});

async function onSubmit(event) {
  console.log(event.data);
}
</script>
```

- ### **Props**

  \- **state** : "string" | "any". This prop is required.

  \- **schema** : use with Zod. The default prop set **undefined**.

---
