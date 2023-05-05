<script setup>
const formData = ref({
    username: "",
    password: "123321",
});

async function handleSubmit(data) {
    await wait(3000);
    console.log(data);
}

async function username_is_unique(node) {
    const usernames = [
        "jzapata",
        "luanguyen",
        "daniel",
    ]
    return !usernames.includes(node.value);
}
</script>

<template>
    <div>

        <!-- custom validations -->
        <FormKit
                type="form"
                submit-label="Login"
                :value="formData"
                @submit="handleSubmit"
        >
            <template #default="{state}">
                <h1>Login</h1>
                <!-- We can create the validations on formkit.config.ts
                and also include language specific messages -->
                <FormKit
                        validation="(500)username_is_unique"
                        :validation-rules="{ username_is_unique }"
                        :validation-messages="{
                            username_is_unique({name, node}){
                                return `${name}: ${node.value} username is already taken`
                            }
                        }"
                        type="text"
                        label="Username"
                        name="username"
                />

                <FormKit type="password" label="Password" name="password"/>
            </template>
        </FormKit>

        <!-- validations -->
        <FormKit v-if="false"
                 type="form"
                 submit-label="Login"
                 :value="formData"
                 @submit="handleSubmit"
        >
            <template #default="{state}">
                <h1>Login</h1>
                <FormKit
                        validation="required|length:8,20"
                        type="text" label="Username" name="username"/>
                <FormKit type="password" label="Password" name="password"/>
            </template>
        </FormKit>

        <!-- Submit form - Customize form via template slot -->
        <FormKit v-if="false"
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
