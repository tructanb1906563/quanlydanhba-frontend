<template>
<div class="page">
         <h4>Thêm liên hệ mới</h4>
        <ContactForm :contact="contact" @submit:contact="AddContactNew"></ContactForm>
</div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
import { object } from 'yup/lib/locale';
    export default {
        components: {
         ContactForm    
        },
        data() {
            return {
                contact: {
                type:object,
                required: true
            },
                };
        },
         methods:{
             AddContactNew(){
                 if(confirm("Bạn có chắc chắn thêm !" )){
                    this.$router.push({ name: "ContactBook" });
                    return ContactService.create(this.contact);
                 }
             }
        }
    };
</script>