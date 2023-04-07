<template>
    <h4>Thêm liên hệ liên hệ</h4>
    <ContactForm 
        :contact="{}"
        @submit:contact="addContact"
    />
    <p>{{ message }}</p>
</template>
<script>
import ContactForm from '@/components/ContactForm.vue'
import ContactService from '@/services/contact.service'

export default {
    components: {
        ContactForm
    },
    data() {
        return {
            contact: '',
            message: ''
        }
    },
    methods: {
        async addContact(data) {
            try {
                await ContactService.create(data)
                this.message = 'Liên hệ được thêm thành công'
            } catch(error) {
                console.log(error)
            }
        }
    },
    created() {
        this.message = ''
    }
}
</script>

