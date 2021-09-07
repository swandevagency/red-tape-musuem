<template>
  <section class="buy-tickets-section">
    <div class="buy-tickets-description-wrapper">
      <img src="/Ticket design.png" alt="" ref="ticketImage" />
      <div
        class="buy-tickets-content"
        @mousemove="interactWithTicketImage"
        @mouseleave="resetTicketImage"
        ref="buyTicketsContent"
      >
        <h2>Buy tickets</h2>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
          eiusmod tempor incididunt ut labore et dolore magna aliqua. Aliquam
          faucibus purus in massa tempor nec feugiat nisl. Ornare arcu odio ut
          sem. Consectetur adipiscing elit pellentesque habitant morbi tristique
          senectus. Eget nunc lobortis mattis aliquam faucibus purus in massa.
        </p>
        <nuxt-link class="section-link-button" to="BuyTickets"
          >BUY TICKETS</nuxt-link
        >
      </div>
    </div>
  </section>
</template>

<script>
export default {
  methods: {
    interactWithTicketImage(event) {
      const cursor = {
        positionX:
          ((event.pageX - this.$refs.buyTicketsContent.offsetLeft) /
            this.$refs.buyTicketsContent.clientWidth -
            0.5) *
          0.1,
        positionY:
          -(
            (event.pageY - this.$refs.buyTicketsContent.offsetTop) /
              this.$refs.buyTicketsContent.clientHeight -
            0.5
          ) * 0.1,
      };
      this.$refs.ticketImage.style.transform = `perspective(0.4em) rotateX(${cursor.positionY}deg) rotateY(${cursor.positionX}deg)`;
    },
    resetTicketImage() {
      this.$refs.ticketImage.style.transform = `perspective(0.4em) rotateX(0deg) rotateY(0deg)`;
    },
  },
};
</script>

<style>
/* #region Buy tickets section */
.buy-tickets-description-wrapper {
  padding: 8em 0 6em;
  display: flex;
  align-items: center;
  flex-direction: column;
}
.buy-tickets-description-wrapper > img {
  transition: transform 0.5s ease-out;
  width: 30%;
}
.buy-tickets-content {
  margin: 8em 0;
  width: 40%;
  text-align: center;
  position: relative;
  color: var(--light-text-color);
}
.buy-tickets-content > h2 {
  font-size: 34px;
  margin: 0 0 0.5em;
  font-family: "Adobe Jenson Pro";
  font-weight: 300;
}
.buy-tickets-content > p {
  font-family: montserrat;
  margin: 0;
  line-height: 30px;
  font-weight: 300;
}
.buy-tickets-content::before {
  content: "";
  background-color: var(--background-color);
  top: -2em;
  bottom: -2em;
  left: -2em;
  right: 0em;
  box-sizing: border-box;
  position: absolute;
  z-index: -1;
}
.buy-tickets-content::after {
  content: "";
  border: 3px solid var(--primary-theme-color);
  top: -4em;
  bottom: -4em;
  left: 2em;
  right: 2em;
  box-sizing: border-box;
  position: absolute;
  z-index: -2;
}
/* #endregion */
</style>