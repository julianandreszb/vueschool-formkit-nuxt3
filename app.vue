<template>
  <div>
      <FormKit
              label="Username"
              name="username"
              type="text"
              help="Pick a new username"
              validation="required:matches:/^@[a-ZA-Z]+$/|length:5"
              value="@useFormKit"
              prefix-icon="avatarMan"
              inner-class="mycustom-inner">
          <template #label="context">
              {{ context.label }} ?
 0             <span>{{ context.help }}</span>
          </template>
      </FormKit>
  </div>
</template>
