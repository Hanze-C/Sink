<script setup>
import { toast } from 'vue-sonner'

const props = defineProps({
  link: {
    type: Object,
    required: true,
  },
})

const emit = defineEmits(['update:link'])

async function deleteLink() {
  await useAPI('/api/link/delete', {
    method: 'POST',
    body: {
      slug: props.link.slug,
    },
  })
  emit('update:link', props.link, 'delete')
  toast('Delete successful!')
}
</script>

<template>
  <AlertDialog>
    <AlertDialogTrigger as-child>
      <slot />
    </AlertDialogTrigger>
    <AlertDialogContent class="max-w-[95svw] max-h-[95svh] md:max-w-lg grid-rows-[auto_minmax(0,1fr)_auto]">
      <AlertDialogHeader>
        <AlertDialogTitle>你确认删除吗?</AlertDialogTitle>
        <AlertDialogDescription>
          此操作不可撤销，将从服务器中删除该链接。
        </AlertDialogDescription>
      </AlertDialogHeader>
      <AlertDialogFooter>
        <AlertDialogCancel>取消</AlertDialogCancel>
        <AlertDialogAction @click="deleteLink">
          删除
        </AlertDialogAction>
      </AlertDialogFooter>
    </AlertDialogContent>
  </AlertDialog>
</template>
