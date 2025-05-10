<template>
    <div>
        <h2>제목목</h2>
        <p>ㄴㄴㄴㄴ</p>
        <p>content</p>
        <p class="text-muted">2020-01-01</p>
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
import { useRoute, useRouter } from 'vue-router'
import { getPostById } from '@/api/posts'
import { ref } from 'vue'

// const props = defineProps({
//     id: [String, Number],
// })

const route = useRoute()
const router = useRouter()
const id = route.params.id
const form = ref({})

const fetchPosts = () => {
    const data = getPostById(id)
    form.value = { ...data }
}

const goListPage = () => router.push({ name: 'PostList' })
const goEditPage = () => router.push({ name: 'PostEdit', params: { id } })
</script>

<style lang="scss" scoped></style>
