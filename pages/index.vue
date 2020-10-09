<template>
  <div class="min-h-screen flex items-center justify-center">
    <button @click="checkout" class="bg-indigo-500 text-white px-4 py-2 text-xl rounded">Pay Now</button>
  </div>
</template>
<script>
export default {
  methods: {
    checkout() {
      const rzp_options = {
        key: "rzp_test_o9cMykk3uCzB0C",
        amount: 400,
        currency: "INR",
        name: "Testing",
        description: "Testing Description",
        handler: function (response) {
          alert(`Payment Succesful ${response.razorpay_payment_id}`);
        },
        modal: {
          ondismiss: function () {
            alert(`Payment Failed`);
          },
        },
        theme: {
          color: "#667eea",
        },
      };
      const rzp1 = new Razorpay(rzp_options);
      console.log(rzp_options);
      console.log(rzp1);
      rzp1.open();
    },
  },
};
</script>