<template>
  <div>
    <div id="banner"></div>
    <div id="intro-body">
      <div class="description">
        <h2 class="menu-txt">Why Home Cook</h2>
        <span>
          <p>
            Home cook connect home chef with people that are searching for
            quality home food. Cook up a dish and share it to reach prospective
            diners. Dine with thousands of home cook menu and have it delivered
            or picked up. With Home Cook, everyone can be a chef.
          </p>
        </span>
      </div>
      <div class="description">
        <iframe
          src="https://www.youtube.com/embed/bKOTKHtbM54"
          scrolling="no"
          frameborder="0"
        ></iframe>
      </div>
    </div>
  </div>
</template>

<script></script>

<style>
#banner {
  object-fit: cover;
  width: 100%;
  height: 382px;
  background: url("https://i.ibb.co/n1mQR7D/110060-00-2x.png");
  background-size: cover;
}

#intro-body {
  display: flex;
  padding-left: 10%;
  padding-right: 10%;
  margin-top: 15px;
}

.description {
  padding-left: 10%;
}

p {
  min-width: 200px;
  min-height: 200px;
  max-width: 300px;
  font-family: "Lato";
  line-height: 20px;
  font-size: 18px;
}

iframe {
  margin-top: 25px;
  min-width: 300px;
  min-height: 200px;
  max-width: 300px;
}

@media screen and (max-width: 700px) {
  .description {
    padding-left: 0%;
  }

  p {
    min-height: 10px;
    min-width: 100%;
  }

  iframe {
    margin-top: 10px;
    min-width: 100%;
    min-height: 250px;
  }

  #intro-body {
    flex-direction: column;
  }
}
</style>
