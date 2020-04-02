<template>
    <el-form :model="trance" :rules="rules">
        <el-form-item prop="data">
            <el-input
                v-model="data"
                onkeypress="return(/[0-9]/.test(String.fromCharCode(event.keyCode)))"
            ></el-input>
        </el-form-item>
    </el-form>
</template>
<script>
export default {
    data() {
        return {
            trance: {
                data: ""
            },
            rules: {
                data: {
                    validator(rule, value, callback) {
                        if (
                            Number.isInteger(Number(value)) &&
                            Number(value) >= 0 &&
                            Number(value) <= 3000
                        ) {
                            callback();
                        } else {
                            callback(new Error("最大数值范围3000"));
                        }
                    },
                    trigger: 'change'
                }
            }
        };
    }
};
</script>