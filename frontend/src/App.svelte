<script>
  let message = "";  // 기본값을 빈 문자열로 설정

  fetch("http://127.0.0.1:8000/hello")
    .then((response) => {
      if (!response.ok) {
        throw new Error("네트워크 응답에 문제가 발생했습니다.");
      }
      return response.json();
    })
    .then((json) => {
      message = json.message;
      console.log(message);
    })
    .catch((error) => {
      console.error("fetch 요청 오류:", error);
    });
</script>

{#if message}
  <h1>{message}</h1>  <!-- message가 존재할 때만 출력 -->
{:else}
  <h1>로딩 중...</h1>  <!-- message가 없으면 "로딩 중..." 표시 -->
{/if}
