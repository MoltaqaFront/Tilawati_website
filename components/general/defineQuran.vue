<template>
  <div id="define_quran" class="services_section_content_wrapper">
    <div class="container-xl">
      <div class="row justify-content-center">
        <div class="service_card" data-aos-once="false" data-aos="fade" :data-aos-delay="'300' * (index + 1)"
          data-aos-duration="1000">
          <p class="card_title">التعريف بالقرآن الكريم</p>
          <div class="card_desc">
            القرآن الكريم هو كلام الله تعالى نزل به جبريل الأمين على قلب نبينا محمد صلى الله عليه وسلم ، لفظه معجز
            وتلاوته بحرفه وكلمه عبادة، نقل إلينا بتواتر السند وكتب في المصاحف، من أول سورة الفاتحة إلى آخر سورة الناس.
            وهو كتاب الله وحبله المتين، فيه نبأ من كان قبلنا وخبر من بعدنا وحكم ما بيننا. وهو الفصل ليس بالهزل، وهو
            الذكر الحكيم والصراط المستقيم، من ابتغى الهدى في غيره أضله الله.
            نزل القرآن بلسان عربي مبين {قُرۡءَانًا عَرَبِيًّا غَيۡرَ ذِي عِوَجٖ لَّعَلَّهُمۡ يَتَّقُونَ} و تعهد الله
            بحفظه {إِنَّا نَحۡنُ نَزَّلۡنَا ٱلذِّكۡرَ وَإِنَّا لَهُۥ لَحَٰفِظُونَ} ويسر للعالمين تلاوته وذكره {وَلَقَدۡ
            يَسَّرۡنَا ٱلۡقُرۡءَانَ لِلذِّكۡرِ فَهَلۡ مِن مُّدَّكِرٖ} وهو غاية في الإعجاز {قُل لَّئِنِ ٱجۡتَمَعَتِ
            ٱلۡإِنسُ وَٱلۡجِنُّ عَلَىٰٓ أَن يَأۡتُواْ بِمِثۡلِ هَٰذَا ٱلۡقُرۡءَانِ لَا يَأۡتُونَ بِمِثۡلِهِۦ وَلَوۡ
            كَانَ بَعۡضُهُمۡ لِبَعۡضٖ ظَهِيرٗا} وأمرنا المولى بقراءته {فَٱقۡرَءُواْ مَا تَيَسَّرَ مِنَ ٱلۡقُرۡءَانِ}
            وترتيله {وَرَتِّلِ ٱلۡقُرۡءَانَ تَرۡتِيلًا} بل وتدبره {أَفَلَا يَتَدَبَّرُونَ ٱلۡقُرۡءَانَ أَمۡ عَلَىٰ
            قُلُوبٍ أَقۡفَالُهَآ} وحذر من هجره{وَقَال ٱلرَّسُولُ يَٰرَبِّ إِنَّ قَوۡمِي ٱتَّخَذُواْ هَٰذَا ٱلۡقُرۡءَانَ
            مَهۡجُورٗا} وكيف لا وهو الكتاب الذي تخشاه الجبال {لَوۡ أَنزَلۡنَا هَٰذَا ٱلۡقُرۡءَانَ عَلَىٰ جَبَلٖ
            لَّرَأَيۡتَهُۥ خَٰشِعٗا مُّتَصَدِّعٗا مِّنۡ خَشۡيَةِ ٱللَّهِ‌ۚ وَتِلۡكَ ٱلۡأَمۡثَٰلُ نَضۡرِبُهَا لِلنَّاسِ
            لَعَلَّهُمۡ يَتَفَكَّرُونَ}وهو من أعظم شعائر الله {ذَٰلِكَ‌ۖ وَمَن يُعَظِّمۡ شَعَٰٓئِرَ ٱللَّهِ فَإِنَّهَا
            مِن تَقۡوَى ٱلۡقُلُوبِ}.
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "ServicesSection",
};
</script>

<style lang="scss" scoped>
.services_section_content_wrapper {
  background-color: #f8f8f8;
  padding-block: 80px 20px;

  .row {
    div[class*="col-"] {
      &:nth-child(2) {
        .service_card {
          transform: translateY(-60px);
        }
      }
    }

    .service_card {
      padding: 15px;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      row-gap: 20px;

      .icon {
        object-fit: cover;
      }

      .card_title {
        margin: 0;
        font-size: 1.5rem;
        font-weight: 700;
        color: var(--secondary_theme_clr);
      }

      .card_desc {
        word-break: break-word;
        word-spacing: 2px;
        font-size: 16px;
        color: var(--light_gray_clr);
        line-height: 1.6;
        text-align: center;
        width: 80%;
      }

      .links_wrapper {
        @include flexCenterAlignment;
        column-gap: 10px;
        row-gap: 10px;
      }
    }
  }
}

@media (max-width: 850px) {
  .services_section_content_wrapper {
    padding-block: 20px;

    .row {
      div[class*="col-"] {
        &:nth-child(2) {
          .service_card {
            transform: translateY(0);
          }
        }
      }
    }
  }
}
</style>
