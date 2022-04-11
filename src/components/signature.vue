<template>
  <div class="container mt-5 col-md-4">
    <div class="card shadow p-3 mb-5 bg-white rounded">
      <div class="text-center">
        <img src="@/assets/tatilmaximum.logo.png" class="img-fluid" alt="" />
      </div>

      <div class="row mt-2">
        <div class="col-lg-6 text-center">
          <img src="@/assets/maxirez.logo.png" class="logoMaxiRez" alt="" />
        </div>

        <div class="col-lg-6 text-center pt-2">
          <img
            src="@/assets/resclick.logo.png"
            class="logoResClick pe-4"
            alt=""
          />
        </div>
      </div>

      <div class="card-body">
        <form>
          <div class="mb-3">
            <select class="form-select" v-model="selectedCompany">
              <option value="null" disabled hidden>Şirket Seçiniz</option>
              <option v-for="(company, index) in companies" :key="index">
                {{ company }}
              </option>
            </select>
          </div>

          <div class="mb-3">
            <input
              v-model="employeeName"
              type="text"
              class="form-control"
              placeholder="Lütfen Adınızı ve Soyadınızı Giriniz"
            />
          </div>

          <div class="mb-3">
            <select class="form-select" v-model="employeeTitle">
              <option value="null" disabled hidden>
                İş Tanımınızı Seçiniz
              </option>
              <option v-for="(title, index) in titles" :key="index">
                {{ title }}
              </option>
            </select>
          </div>
        </form>

        <div class="d-flex justify-content-between">
          <button
            id="btnCopySignature"
            type="button"
            class="btn btn-success btn-sm btn-block copy"
            data-clipboard-target="#signature"
            @click="copySignature()"
          >
            Copy Signature
          </button>

          <button
            type="button"
            class="btn btn-primary btn-sm btn-block"
            @click="copyHtml()"
          >
            Copy HTML
          </button>

          <button
            type="button"
            class="btn btn-warning btn-sm btn-block"
            @click="saveAs()"
          >
            Save As
          </button>
        </div>
      </div>
    </div>
  </div>

  <div class="container col-md-4">
    <div
      id="signature"
      style="font-family: Tahoma, sans-serif, Times New Roman; font-size: 12px"
    >
      <p><b>Saygılarımla - Best Regards </b></p>
      <p>
        <b
          >{{ employeeName }} <br /><span style="color: grey">
            {{ employeeTitle }}</span
          ></b
        >
      </p>

      <img
        width="180"
        src="https://maxirez.com/images/maxirez.png"
        v-if="selectedCompany === 'Maxi Rez'"
      />

      <img
        width="200"
        src="https://i.imgur.com/LSPfsmd.png"
        v-else-if="selectedCompany === 'Tatil Maximum'"
      />

      <img
        width="180"
        src="https://i.imgur.com/NYcJ5VE.png"
        v-else-if="selectedCompany === 'ResClick'"
      />

      <br />
      <br />
      <b v-if="selectedCompany === 'Tatil Maximum'"
        >Tatilmaximum Tur. ve Tic. Ltd. Şti.</b
      >
      <b v-else-if="selectedCompany === 'ResClick'">ResClick Yazılım</b>
      <b v-else-if="selectedCompany === 'Maxi Rez'"
        >Bertouristic İnş. Org. Ltd. Şti.</b
      >


      <p v-if="selectedCompany === 'Tatil Maximum'">
        Güzeloba Mahallesi, Çağlayangil Caddesi No: 10/A <br />
        07230 Muratpaşa/Antalya
      </p>
      <p v-else-if="selectedCompany === 'ResClick'">
        Güzeloba Mahallesi, Çağlayangil Caddesi No: 10/A <br />
        07230 Muratpaşa/Antalya
      </p>
      <p v-else-if="selectedCompany === 'Maxi Rez'">
        Güzeloba Mahallesi, Çağlayangil Caddesi No: 10/B <br />
        07230 Muratpaşa/Antalya
      </p>

      <table
        border-collapse="collapse"
        style="
          font-family: Tahoma, sans-serif, Times New Roman;
          font-size: 12px;
        "
      >
        <tr>
          <td style="width: 100px; border: none">Call Center</td>
          <td style="text-align: right; border: none">:</td>
          <td style="width: 200px; border: none">+90 850 300 0 444</td>
        </tr>
        <tr>
          <td style="border: none">Tel</td>
          <td style="text-align: right; border: none">:</td>
          <td style="border: none">+90 242 324 3 339</td>
        </tr>
        <tr>
          <td style="border: none">E-Mail</td>
          <td style="text-align: right; border: none">:</td>
          <td style="border: none">
            <a
              v-if="selectedCompany === 'Maxi Rez'"
              href="mailto: info@maxirez.com"
            >
              info@maxirez.com</a
            >

            <a
              v-else-if="selectedCompany === 'Tatil Maximum'"
              href="mailto: info@tatilmaximum.com.tr"
            >
              info@tatilmaximum.com.tr</a
            >

            <a
              v-else-if="selectedCompany === 'ResClick'"
              href="mailto: info@resclick.com"
            >
              info@resclick.com</a
            >
          </td>
        </tr>
        <tr>
          <td style="border: none">Web</td>
          <td style="text-align: right; border: none">:</td>
          <td style="border: none">
            <a v-if="selectedCompany === 'Maxi Rez'" href="https://maxirez.com/"
              >www.maxirez.com</a
            >
            <a
              v-else-if="selectedCompany === 'Tatil Maximum'"
              href="http://www.tatilmaximum.com.tr/"
              >www.tatilmaximum.com.tr</a
            >
            <a
              v-else-if="selectedCompany === 'ResClick'"
              href="https://resclick.com/"
              >www.resclick.com</a
            >
          </td>
        </tr>
      </table>

      <p>
        Bu e-postanın içeriği gizlidir ve yalnızca mesajda belirtilen alıcıya
        yöneliktir. Gönderenin yazılı izni olmaksızın bu mesajın herhangi bir
        kısmının herhangi bir üçüncü şahıs ile paylaşılması kesinlikle yasaktır.
        Bu mesajı yanlışlıkla aldıysanız, lütfen bu mesajı yanıtlayın ve
        silinmesini takip edin, böylece gelecekte böyle bir hatanın meydana
        gelmemesini sağlayabiliriz.
      </p>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import useClipboard from 'vue-clipboard3';

export default defineComponent({
  data() {
    return {
      selectedCompany: null,
      employeeTitle: null,
      employeeName: null,
      companies: ['Maxi Rez', 'ResClick', 'Tatil Maximum'],
      titles: [
        'Çağrı Merkezi Müşteri Temsilcisi',
        'Satış Sonrası Destek Temsilcisi',
        'Takım Lideri',
        'Çağrı Merkezi Şefi',
        'Fiyatlandırma Şefi',
        'Kontrat Asistanı',
        'Kontrat Müdürü',
        'Rezervasyon Sorumlusu',
        'Fiyatlandırma Sorumlusu',
        'Kalite ve Eğitim Sorumlusu',
        'Krediler Şefi',
        'Muhasebe Şefi',
        'Finans Sorumlusu',
        'Finans Müdürü',
        'Operasyon Müdür Yardımcısı',
      ],
    };
  },

  methods: {
    async copyHtml() {
      const { toClipboard } = useClipboard();
      const div = document.querySelector('#signature')!.innerHTML;

      await toClipboard(div);
    },

    copySignature() {
      const selection = window.getSelection()!;
      const div = document.querySelector('#signature')!;

      if (selection.rangeCount > 0) {
        selection.removeAllRanges();
      }

      const range = document.createRange();
      range.selectNode(div);
      selection.addRange(range);
      document.execCommand('copy');
      selection.removeAllRanges();
    },

    saveAs() {
      const div = document.querySelector('#signature')?.innerHTML;
      const element = document.createElement('a');

      element.setAttribute('href', 'data:text/plain;charset=utf-8,' + div);
      element.setAttribute('download', 'signature.html');

      element.style.display = 'none';
      document.body.appendChild(element);

      element.click();

      document.body.removeChild(element);
    },
  },
});
</script>

<style scoped>
.img {
  height: auto;
  width: 200px;
}

.logoResClick {
  height: auto;
  width: 250px;
}
.logoMaxiRez {
  height: auto;
  width: 200px;
}
.logoTatilMax {
  height: auto;
  width: auto;
}
</style>
