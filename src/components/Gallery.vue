<script setup="setup">
    import {ref, onMounted, onUnmounted} from 'vue'

    import pict1 from '@/assets/picture/pict1.jpeg'
    import pict2 from '@/assets/picture/pict2.jpeg'
    import pict3 from '@/assets/picture/pict3.jpeg'
    import pict4 from '@/assets/picture/pict4.jpeg'
    import pict5 from '@/assets/picture/pict5.jpeg'
    import pict6 from '@/assets/picture/pict6.jpeg'
    import pict7 from '@/assets/picture/pict7.jpeg'
    import pict8 from '@/assets/picture/pict8.jpeg'
    import bgGallery from '@/assets/picture/background2.png'

    const photos = [
        pict1,
        pict2,
        pict3,
        pict4,
        pict5,
        pict8,
        pict6,
        pict7
    ]

    const visible = ref(false)
    let observer = null

    onMounted(() => {
        const section = document.querySelector('.gallery')

        observer = new IntersectionObserver((entries) => {
            entries.forEach((entry) => {
                visible.value = entry.isIntersecting
            })
        }, {threshold: 0.2})

        if (section) 
            observer.observe(section)
    })

    onUnmounted(() => {
        if (observer) 
            observer.disconnect()
    })
</script>

<template>
    <section
        class="gallery"
        :class="{ visible }"
        :style="{ backgroundImage: `url(${bgGallery})` }">

        <!-- Header -->
        <div class="section-header">

            <div class="header-ornament">
                <svg width="40" height="20" viewBox="0 0 40 20" fill="none">
                    <path d="M0 10 L15 10 M25 10 L40 10" stroke="#d4b483" stroke-width="1"/>

                    <path
                        d="M20 1 L21 9 L29 10 L21 11 L20 19 L19 11 L11 10 L19 9 Z"
                        fill="#d4b483"/>
                </svg>
            </div>

            <h2 class="section-title">
                Gallery
            </h2>

            <p class="section-subtitle">
                Momen kebahagiaan kami
            </p>

        </div>

        <!-- Gallery -->

        <div class="photo-grid">

            <div
                v-for="(photo,index) in photos"
                :key="index"
                class="photo-item"
                :class="`photo-${index + 1}`"
                data-aos="fade-up"
                :data-aos-delay="index * 120">

                <img :src="photo" :alt="`Photo ${index + 1}`" loading="lazy"></div>

            </div>

            <!-- Bottom Ornament -->

            <div class="bottom-decoration">

                <svg width="60" height="30" viewBox="0 0 60 30" fill="none">

                    <path d="M0 15 L20 15 M40 15 L60 15" stroke="#d4b483" stroke-width="1"/>

                    <path
                        d="M30 5 L32 13 L40 15 L32 17 L30 25 L28 17 L20 15 L28 13 Z"
                        fill="#d4b483"/>

                </svg>

            </div>

        </section>
    </template>

    <style scoped="scoped">
        .gallery {
            padding: 60px 22px;
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            display: flex;
            flex-direction: column;
            align-items: center;
            position: relative;
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }

        .gallery.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* ================= HEADER ================= */

        .section-header {
            text-align: center;
            margin-bottom: 40px;
        }

        .header-ornament {
            margin-bottom: 12px;
        }

        .section-title {
            font-family: 'Playfair Display',serif;
            font-size: 32px;
            font-weight: 500;
            color: #2d2d2d;
            margin-bottom: 8px;
        }

        .section-subtitle {
            font-family: 'Lato',sans-serif;
            color: #8f8474;
            font-size: 14px;
            letter-spacing: 1px;
        }

        /* ================= GRID ================= */

        .photo-grid {
            width: 100%;
            max-width: 470px;
            display: grid;
            grid-template-columns: repeat(2,1fr);
            gap: 14px;
        }

        /* ================= CARD ================= */

        .photo-item {

            overflow: hidden;

            border-radius:22px;
            
            background: white;

            box-shadow: 0 8px 25px rgba(0,0,0,.06), 0 2px 8px rgba(0,0,0,.05);

            transition: transform 0.35s, box-shadow 0.35s;

            border: 4px solid rgba(255,255,255,.85);
        }

        .photo-item:hover {

            transform: translateY(-6px);

            box-shadow: 0 14px 30px rgba(0,0,0,.15);

        }

        .photo-item img {

            width: 100%;

            height: 100%;

            object-fit: cover;

            transition: 0.45s;

        }

        .photo-item:hover img {

            transform: scale(1.05);

        }

        /* ================= HEIGHT ================= */

        /* pict1 */
        .photo-1 {
            height: 240px;
        }

        /* pict2 */
        .photo-2 {
            height: 185px;
        }

        /* pict3 */
        .photo-3 {
            height: 225px;
        }

        /* pict4 */
        .photo-4 {
            height: 185px;
        }

        /* pict5 */
        .photo-5 {
            height: 235px;
        }

        /* pict8 */
        .photo-6 {
            height: 235px;
        }

        /* pict6 */
        .photo-7 {
            height: 220px;
        }

        /* pict7 */
        .photo-8 {
            height: 185px;
        }

        /* ================= CROP ================= */

        /* pict1 */
        .photo-1 img {
            object-position: center center;
        }

        /* pict2 */
        .photo-2 img {
            object-position: center 30%;
        }

        /* pict3 */
        .photo-3 img {
            object-position: center center;
        }

        /* pict4 */
        .photo-4 img {
            object-position: center bottom;
        }

        /* pict5 */
        .photo-5 img {
            object-position: center center;
        }

        /* pict8 */
        .photo-6 img {
            object-position: center 20%;
        }

        /* pict6 */
        .photo-7 img {
            object-position: center 25%;
        }

        /* pict7 */
        .photo-8 img {
            object-position: center bottom;
        }

        /* ================= DECORATION ================= */

        .bottom-decoration {
            margin-top: 50px;
        }

        /* ================= MOBILE ================= */

        @media(max-width:480px) {

            .gallery {

                padding: 50px 18px;

            }

            .photo-grid {

                gap: 12px;

            }

            .photo-1 {

                height: 220px;

            }

            .photo-2 {

                height: 170px;

            }

            .photo-3 {

                height: 205px;

            }

            .photo-4 {

                height: 170px;

            }

            .photo-5 {

                height: 215px;

            }

            .photo-6 {

                height: 215px;

            }

            .photo-7 {

                height: 200px;

            }

            .photo-8 {

                height: 170px;

            }

        }

        @media(max-width:360px) {

            .gallery {

                padding: 45px 14px;

            }

            .photo-grid {

                gap: 10px;

            }

            .photo-item {

                border-radius: 14px;

            }

            .photo-item:active img {
                transform: scale(1.05);
            }

        }
    </style>