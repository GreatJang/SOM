<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-white shadow-sm">
    <div class="container-fluid">
      <div class="navbar-collapse w-100 order-1 order-md-0 dual-collapse2">
        <ul class="navbar-nav mr-auto" v-if="userRole === 'ADMIN'">
          <li class="nav-item">
            <a class="nav-link text-3xs font-bold mb-1" href="/members">회원관리</a>
          </li>
          <li class="nav-item">
            <a class="nav-link text-3xs font-bold mb-1" href="/posts/manage">게시글 관리</a>
          </li>
        </ul>
      </div>
      <div class="mx-auto order-0">
        <a href="/">
          <img style="width:300px" src="@/assets/som.png"/>
        </a>
      </div>
      <div class="navbar-collapse w-100 order-3 dual-collapse2">
        <ul class="navbar-nav ml-auto">
          <!-- <li class="nav-item">
            <a class="nav-link" href="/posttest">테스트용 페이지</a>
          </li> --> 
          <li class="nav-item">
            <a class="nav-link text-3xs font-bold mb-1" href="/postlist">게시글 목록</a>
          </li>
          <li class="nav-item" v-if="isLogin">
            <a class="nav-link text-3xs font-bold mb-1" href="/mypage">MyPage</a>
          </li>
          <li class="nav-item" v-if="!isLogin">
            <a class="nav-link text-3xs font-bold mb-1" href="/member/create">회원가입</a>
          </li>
          <li class="nav-item" v-if="!isLogin">
            <a class="nav-link text-3xs font-bold mb-1" href="/login">로그인</a>
          </li>
          <li class="nav-item" v-if="isLogin">
            <a class="nav-link text-3xs font-bold mb-1" href="/login" @click="doLogout">로그아웃</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
      return {
          isLogin: false,
          userRole: null
      }
  },
  created() {
      if (localStorage.getItem("token")) {
          this.isLogin = true;
          this.userRole = localStorage.getItem("role");
      }
  },
  methods: {
      doLogout() {
          localStorage.clear();
          window.location.reload();
      }
  },
}
</script>

<style scoped>
/* 추가된 CSS 스타일 */
.navbar {
  border-bottom: none; /* 기존 border 제거 */
}

.navbar-brand img {
  height: 50px; /* 로고 이미지 높이 조절 */
}

.navbar-nav .nav-link {
  color: #333; /* 링크 색상 변경 */
}

.navbar-nav .nav-link:hover {
  color: #555; /* 호버 시 색상 변경 */
}

.shadow-sm {
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1); /* 그림자 효과 추가 */
}
</style>
