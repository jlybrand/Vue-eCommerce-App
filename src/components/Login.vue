<template>
  <transition name="modal-animation">
    <div v-show="loginActive" class="modal">
      <transition name="modal-animation-inner">
        <div v-show="loginActive" class="modal-inner">
          <button @click="close" type="button" class="btn btn-light">X</button>
          <div class="modal-body">
            <div class="tab-content" id="pills-tabContent">
              <form>
                <h5 class="text-center">Log In</h5>

                <div class="form-group">
                  <label for="exampleInputEmail1">Email</label>
                  <input
                    type="email"
                    v-model="email"
                    class="form-control"
                    id="exampleInputEmail1"
                    aria-describedby="emailHelp"
                    placeholder="Enter email"
                  />
                </div>
                <div class="form-group">
                  <label for="exampleInputPassword1">Password</label>
                  <input
                    type="password"
                    @keyup.enter="login"
                    v-model="password"
                    class="form-control"
                    id="exampleInputPassword1"
                    placeholder="Password"
                  />
                </div>
                <ul
                  class="nav nav-fill nav-pills mb-3"
                  id="pills-tab"
                  role="tablist"
                >
                  <li class="nav-item">
                    <a
                      @click="login"
                      class="nav-link active"
                      id="pills-home-tab"
                      data-toggle="pill"
                      href="#pills-login"
                      role="tab"
                      aria-controls="pills-login"
                      aria-selected="true"
                      >Login</a
                    >
                  </li>
                </ul>
              </form>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </transition>
</template>

<script>
export default {
  name: "LoginModal",
  data() {
    return {
      name: null,
      email: null,
      password: null,
    };
  },
  props: ["loginActive"],
  setup(props, { emit }) {
    const close = () => {
      emit("close");
    };

    return { close };
  },
};
</script>

<style scoped>
.modal-animation-enter-active,
.modal-animation-leave-active {
  transition: opacity 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}

.modal-animation-enter-from,
.modal-animation-leave-to {
  opacity: 0;
}

.modal-animation-inner-enter-active {
  transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02) 0.15s;
}

.modal-animation-inner-leave-active {
  transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}

.modal-animation-inner-enter-from {
  opacity: 0;
  transform: scale(0.8);
}

.modal-animation-inner-leave-to {
  transform: scale(0.8);
}

.modal {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 30px;
  left: 0;
  background-color: rgba(255, 255, 255, 0.7);
}
.modal-inner {
  position: relative;
  max-width: 640px;
  width: 80%;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -1px rgba(0, 0, 0, 0.06);
  background-color: #fff;
  padding: 50px 16px;
}

button {
  position: absolute;
  top: 15px;
  right: 15px;
  border-radius: 50%;
  cursor: pointer;
}

button:hover {
  color: crimson;
}

.text-center {
  font-weight: 700;
  font-size: 1.5rem;
  margin-bottom: 30px;
}

.form-control {
  margin-bottom: 20px;
}
</style>
