<script setup>
const formData = ref({
    username: "jzapata",
    password: "123321",
});

async function handleSubmit(data) {
    await wait(3000);
    console.log(data);
}
</script>

<template>
    <div>
        <!-- Submit form - Customize form via template slot -->
        <FormKit
                type="form"
                submit-label="Login"
                :value="formData"
                :actions="false"
                @submit="handleSubmit"
        >
            <template #default="{state}">
                <h1>Login</h1>
                <FormKit type="text" label="Username" name="username"/>
                <FormKit type="password" label="Password" name="password"/>
                <button :disabled="state.loading">
                    {{ state.loading ? "Loading..." : "Login" }}
                </button>
            </template>
        </FormKit>

        <!-- Submit form -->
        <FormKit v-if="false"
                 type="form"
                 submit-label="My Submit button"
                 :value="formData"
                 @submit="handleSubmit"

        >
            <h1>Login</h1>
            <FormKit type="text" label="Username" name="username"/>
            <FormKit type="password" label="Password" name="password"/>
        </FormKit>

        <!-- Using template-->
        <FormKit v-if="false"
                 label="Username"
                 name="username"
                 type="text"
                 help="Pick a new username"
                 validation="required:matches:/^@[a-ZA-Z]+$/|length:5"
                 value="@useFormKit"
                 prefix-icon="avatarMan"
                 inner-class="mycustom-inner">
            <template #label="context">
                {{ context.label }} ? <span>{{ context.help }}</span>
            </template>
        </FormKit>
    </div>
</template>
