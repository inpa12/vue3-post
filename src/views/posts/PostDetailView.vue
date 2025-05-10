<template>
    <div>
        <h2>{{ form.title }}</h2>
        <p>{{ form.content }}</p>
        <p class="text-muted"><p>{{ form.createdAt }}</p></p>
        <hr class="my-4" />
        <div class="row g-2">
            <div class="col-auto">
                <button class="btn btn-outline-dark" @click="$router.push('/posts/10')">
                    이전글
                </button>
            </div>
            <div class="col-auto">
                <button class="btn btn-outline-dark" @click="$router.push('/posts/11')">
                    다음글
                </button>
            </div>
            <div class="col-auto me-auto"></div>
            <div class="col-auto">
                <button class="btn btn-outline-dark" @click="goListPage">목록</button>
            </div>
            <div class="col-auto">
                <button class="btn btn-outline-primary" @click="goEditPage">수정</button>
            </div>
            <div class="col-auto">
                <button class="btn btn-outline-danger">삭제</button>
            </div>
        </div>
    </div>
</template>

<script setup>
import { useRouter } from 'vue-router'
import { getPostById } from '@/api/posts'
import { ref } from 'vue'

 const props = defineProps({
     id: [String, Number],
 })

const router = useRouter()
const form = ref({})

const fetchPosts = async () => {
    const { data } = await getPostById(props.id)
    form.value = { ...data }
}
fetchPosts()

const goListPage = () => router.push({ name: 'PostList' })
const goEditPage = () => router.push({ name: 'PostEdit', params: { id:props.id } })
</script>

<style lang="scss" scoped></style>
