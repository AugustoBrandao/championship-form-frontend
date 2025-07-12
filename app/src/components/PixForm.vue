
<script setup lang="ts">
defineProps<{ email: string }>()
</script>

<template>
    <div style="margin-top: 20px;">
      <h3>Pagamento via PIX</h3>
      <p>Chave PIX: <strong>{{ email }}</strong></p>
      <img src="https://www.cjf.jus.br/cjf/corregedoria-da-justica-federal/turma-nacional-de-uniformizacao/QRCODE.png/@@images/e79747cb-a3c3-4742-b9dd-cb8cdb6ff75a.png" alt="QR Code" style="width: 40%; ">
    </div>
</template>