<route lang="yaml">
meta:
footer:
enabled: false
</route>

<script setup lang="ts">
import { customerLogos } from '/@src/data/pages/logos'
import {
  vehicleFeatures,
  carBrands,
  popularCars,
  vehicleVideoFeatures,
  vehicleTestimonials,
} from '/@src/data/pages/vehicle'
import { socialLinks } from '/@src/data/blocks/advanced/social'
</script>

<template>
  <div>
    <HeroZ />

    <LogoMarquee
      :logos="customerLogos"
      compact
    />

    <Section>
      <Container>
        <JumboBlock
          title="On-Demand Fleet"
          subtitle="Our AI automatically reassigns drivers when needed or when better performance is detected. Close your eyes, we handle everything for you."
          punchline="AI Powered 🔥"
        >
          <template #left>
            <MediaCard
              icon="feather:map-pin"
              meta-text="24, Madison Avenue"
              meta-subtext="in 28 minutes"
              meta-stat="2.3 Miles"
              image="data:image/gif;base64,replace_with_your_image"
              image-width="800"
              image-height="600"
            />
          </template>
          <template #right>
            <MediaCard
              icon="feather:map"
              icon-color="orange"
              meta-text="112, Manhattan Avenue"
              meta-subtext="in 16 minutes"
              meta-stat="1.3 Miles"
              image="data:image/gif;base64,replace_with_your_image"
              image-width="800"
              image-height="600"
            />
          </template>
        </JumboBlock>

<!--        <ContentBlockA-->
<!--          :title="carBrands.title"-->
<!--          :text="carBrands.text"-->
<!--          link="/"-->
<!--          :images="carBrands.images"-->
<!--        />-->
      </Container>
    </Section>

  



    <Section>
      <Container>
        <SectionTitle
          title="Nos voitures"
        />

        <VehicleSlider :slides="popularCars" />
      </Container>
    </Section>

<!--    <Section-->
<!--      wave="wave-1"-->
<!--      shape-color="grey"-->
<!--    >-->
<!--      <Container>-->
<!--        <SectionTitle-->
<!--          title="Start a road trip"-->
<!--          subtitle="Go Wild"-->
<!--        />-->

<!--        <VideoBlockB-->
<!--          title="Our Product"-->
<!--          :features="vehicleVideoFeatures"-->
<!--          source="/assets/video/meeting.mp4"-->
<!--          poster="data:image/gif;base64,replace_with_your_image"-->
<!--        />-->
<!--      </Container>-->
<!--    </Section>-->

    <Section
      color="grey"
      wave="wave-1"
      shape-color="white"
    >
      <Container>
        <SectionTitle
          title="Ce que disent nos clients..."
        />

        <TestimonialCards :items="vehicleTestimonials" />

        <CompanyGrid
          class="-mt-6"
          title="We work with the best"
          subtitle="From the best companies"
          :logos="customerLogos"
          :limit="20"
        />
      </Container>
    </Section>



<!--    <FooterD-->
<!--      text="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Negare-->
<!--              non possum. Apparet statim, quae sint officia, quae actiones."-->
<!--      color="light"-->
<!--      :social-links="socialLinks"-->
<!--    />-->
  </div>
</template>
