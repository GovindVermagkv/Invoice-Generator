<template>
  <div class="container-fluid" v-if="isPreview">
    <!-- <div class="container"> -->
    <table class="table shadow w-100 p-3" id="table">
      <thead>
        <tr class="table-borderless">
          <!-- Header row with company details and logo -->
          <th colspan="4" class="header-details">
            <div class="header-content">
              <br>
              <div class="my-1">U85500UP2023PTC189793</div><br>
              <div class="my-1">A-41, 5th Floor, Tower C, The Iconic Corenthum Building, Sector 62, Noida, Uttar
                Pradesh - 201301</div><br>
              <div class="my-1">Email: info@earlyskillsapp.com</div><br>
            </div>
          </th>
          <th class="logo" colspan="4" @click="downloadInvoice">
            <img id="companyLogo" src="../assets/logo early skill (2).png" alt="Logo" height="100" width="100">
          </th>
        </tr>
      </thead>
      <tbody>
       
        <tr>
          <td>Student Name:</td>
          <td colspan="4">{{ student.name }}</td>
        </tr>
        <tr>
          <td>Address:</td>
          <td colspan="4">{{ student.address }}</td>
        </tr>
        <tr>
          <td>Batch ID:</td>
          <td colspan="4">{{ student.batch_id }}</td>
        </tr>
        <tr>
          <td>Programme Name:</td>
          <td colspan="4">{{ student.programme }}</td>
        </tr>
        <tr>
          <td>Mobile Number:</td>
          <td colspan="4">{{ student.mobile }}</td>
        </tr>
        <tr>
          <td>Email Id:</td>
          <td colspan="4">{{ student.email }}</td>
        </tr>
        <tr>
          <th colspan="5" class="make_left">INVOICE Details</th>
        </tr>
        <tr>
          <td>Payment Id:</td>
          <td colspan="4">{{ student.payment_id }}</td>
        </tr>
        <tr>
          <td>INVOICE Number:</td>
          <td colspan="4">{{ student.invoice_number }}</td>
        </tr>
        <tr>
          <td>INVOICE Date:</td>
          <td colspan="4">{{ student.current_date }}</td>
        </tr>
        <!-- <tr>
          <th colspan="5" class="text-center">INVOICE Items</th>
        </tr> -->
        <tr>
          <th>S.No</th>
          <th>Description</th>
          <th>Taxable Value</th>
          <th>IGST (18%)</th>
          <th>INVOICE Value</th>
        </tr>
        <tr>
          <td>1</td>
          <td>Commercial Training and Coaching Services</td>
          <td>{{ student.course_price }}</td>
          <td>{{ student.course_gst }}</td>
          <td>{{ student.course_Total }}</td>
        </tr>
        <tr>
          <th colspan="5" class="make_left">Bank Details</th>
        </tr>
        <tr>
          <td>Account Holder's Name:</td>
          <td colspan="4">Early Skills Labs Private Limited</td>
        </tr>
        <tr>
          <td>Bank Name:</td>
          <td colspan="4">Axis Bank</td>
        </tr>
        <tr>
          <td>Account Number:</td>
          <td colspan="4">923020030946417</td>
        </tr>
        <tr>
          <td>IFSC code:</td>
          <td colspan="4">UTIB0004914</td>
        </tr>

        <tr class="text-right w-100">
          <th colspan="5" class="signature text-right w-100">Authorised Signatory</th>
        </tr>
        <tr>
          <td colspan="5" class="text-center signature">
            <img src="../assets/sign3.png" alt="Signature" height="80" width="150">
          </td>
        </tr>
        <!-- <tr class="text-right w-100">
          <th colspan="5" class="signature text-right w-100">Authorised Signatory</th>
        </tr>
        <tr>
          <td colspan="5" class="text-center signature">
            <img src="../assets/logo early skill (2).png" alt="Signature" style="width: 150px;">
          </td>
        </tr> -->
      </tbody>
      <!-- <tfoot class="">
          <tr class="text-right w-100">
            <th colspan="5" class="signature text-right w-100">Authorised Signatory</th>
          </tr>
          <tr>
            <td colspan="5" class="text-center signature">
              <img src="../assets/sign.png" alt="Signature" height="80" width="150">
            </td>
          </tr>
        </tfoot> -->
    </table>

    <!-- <button class="btn btn-success"  v-if="showDownload">Download</button> -->
  </div>
  <!-- </div> -->
  <div class="container" v-else>
    <!-- <div class="headers text-center"> -->
      <h3 class="text-right"><span class="text-success">Hello , </span> Anshulika</h3>
    <img src="../assets/logo early skill (2).png" alt="" class="text-center mt-3" height="100" width="100">
    <!-- </div> -->
    <h2 class="my-5">Student Invoice Generator</h2>
    <button @click="openForm" class="btn btn-success">Create Invoice</button>

    <!-- Modal -->
    <div class="modal fade" :class="{ 'show': showModal }">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="studentFormModalLabel">Student Registration Form</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close" @click="closeForm">
              <span aria-hidden="true" class="text-danger">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <form @submit.prevent="submitForm">
              <!-- Form fields here -->
              <div class="form-group">
                <div class="formsection">
                  <label for="name">Student Name:</label>
                  <input type="text" class="form-control my-2" id="name" v-model="student.name" required>
                </div>
                <div class="formsection">
                  <label for="name">Student address:</label>
                  <input type="text" class="form-control my-2" id="address" v-model="student.address" required>
                </div>
                <div class="formsection">
                  <label for="name">Student Batch Id:</label>
                  <input type="text" class="form-control my-2" id="batch_id" v-model="student.batch_id" required>
                </div>
                <div class="formsection">
                  <label for="name">Student Programme:</label>
                  <input type="text" class="form-control my-2" id="programme" v-model="student.programme" required>
                </div>
                <div class="formsection">
                  <label for="name">Student Mobile:</label>
                  <input type="number" class="form-control my-2" id="mobile" v-model="student.mobile" required>
                </div>
                <div class="formsection">
                  <label for="name">Student Email:</label>
                  <input type="email" class="form-control my-2" id="email" v-model="student.email" required>
                </div>
                <div class="formsection">
                  <label for="name">Invoice Suffix :</label>
                  <input type="text" class="form-control my-2" id="email" v-model="student.invoice_number" required>
                </div>
                <div class="formsection">
                  <label for="name">Payment Id :</label>
                  <input type="text" class="form-control my-2" id="name" v-model="student.payment_id" required>
                </div>
                <div class="formsection">
                  <label for="name">Course Price:</label>
                  <input type="number" class="form-control my-2" id="email" v-model="student.course_price" required
                    @input="Calculation">
                </div>

              </div>
              <div class="formsection">
                <p><strong>Course Price : </strong>{{ student.course_price || 0 }}</p>
                <p><strong>Total GST : </strong>{{ student.course_gst }}</p>
                <hr>
                <p><strong>Total : </strong>{{ student.course_Total || 0 }}</p>
              </div>
              <!-- Other form fields... -->
              <div class="buttons">

                <button type="submit" class="btn btn-success">Submit</button>
                <button type="submit" class="btn btn-danger" @click="closeForm">Close</button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>


</template>

<script>
// import jsPDF from 'jspdf';
// import 'jspdf-autotable';

// import html2pdf from 'html2pdf.js';

export default {
  name: "INVOICE",
  data() {
    return {
      isPreview: false,
      showModal: false,
      showDownload: true,
      student: {
        name: '',
        address: '',
        batch_id: '',
        programme: '',
        mobile: '',
        email: '',
        invoice_number: 'ES/B/2024-25//BILL/',
        current_date: '',
        course_price: 0,
        course_gst: 0,
        course_Total: 0,
        payment_id:'pay_'
      }
    }
  },
  methods: {
    // downloadInvoice() {
    //   const doc = new jsPDF();

    //   // Add the table to the PDF
    //   doc.autoTable({ html: '.table' });

    //   // Embed the image using base64
    //   const imgData = document.getElementById('companyLogo').src;
    //   const width = 100; // Adjust width as needed
    //   const height = 100; // Adjust height as needed
    //   doc.addImage(imgData, 'PNG', 150, 10, width / 4, height / 4); // Adjust x, y, width, and height as needed

    //   const pdf = doc.output('blob');
    //   const url = window.URL.createObjectURL(pdf);
    //   const a = document.createElement('a');
    //   a.href = url;
    //   a.download = 'INVOICE.pdf';
    //   a.click();
    //   window.URL.revokeObjectURL(url);
    // }

    openForm() {
      // Open the modal
      this.showModal = true;
    },
    Calculation() {
      // if(this.student.course_price == '' || this.student.course_price == null || this.student.course_price == undefined){
      //   this.student.course_price=0
      // }
      this.student.course_gst = (this.student.course_price * 18) / 100;
      this.student.course_Total = parseInt(this.student.course_price) + parseInt(this.student.course_gst)
    },
    closeForm() {
      // Close the modal
      this.showModal = false;
    },
    submitForm() {
      // You can perform any further validation or processing here before submitting the form
      console.log('Submitting form:', this.student);
      // Here you can send the form data to your backend or perform any other actions

      // Close the modal after form submission
      this.isPreview = true
      this.closeForm();
    },

    // downloadInvoice() {
    //   const doc = new jsPDF();

    //   // Debugging statement
    //   console.log("HTML Table:", document.querySelector('.table'));

    //   // Add the table to the PDF
    //   doc.autoTable({ html: '.table', theme: 'grid' }); // You can try different themes like 'grid' or 'striped'

    //   // Embed the image using base64
    //   const imgData = document.getElementById('companyLogo').src;
    //   const width = 100; // Adjust width as needed
    //   const height = 100; // Adjust height as needed

    //   // Debugging statement
    //   console.log("Image Data:", imgData);

    //   doc.addImage(imgData, 'PNG', 160, 18, width / 4, height / 4); // Adjust x, y, width, and height as needed

    //   const pdf = doc.output('blob');
    //   const url = window.URL.createObjectURL(pdf);
    //   const a = document.createElement('a');
    //   a.href = url;
    //   a.download = `${this.student.name}.pdf`;
    //   a.click();
    //   window.URL.revokeObjectURL(url);
    // }

    downloadInvoice() {
      this.downloadInvoice = false

      setTimeout(() => {
        window.print();
      }, 500);
     
    }

  },
  mounted() {
    var currentDate = new Date();

    // Get day, month, and year
    var day = currentDate.getDate();
    var month = currentDate.getMonth() + 1; // Adding 1 because JavaScript months are zero-based
    var year = currentDate.getFullYear();

    // Pad day and month with leading zeros if necessary
    if (day < 10) {
      day = '0' + day;
    }
    if (month < 10) {
      month = '0' + month;
    }

    // Form the date string in dd/mm/yyyy format
    this.student.current_date = day + '/' + month + '/' + year;
  }
};
</script>

<style scoped>
.container-fluid {
  padding: 20px;
}

.table {
  border-collapse: collapse;
  border: 1px solid black;
  font-size: 8px !important;
}

.table th,
.table td {
  border: 1px solid black;
  padding: 10px;
  text-align: left;
}

.make_left {
  text-align: left !important;
}

.buttons {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 20px 0px;
}

.formsection {
  text-align: left !important;
}

.formsection input {
  text-transform: capitalize;
}

#email {
  text-transform: none;
}

/* .table th{
  height: 200px !important;

} */
thead {
  text-align: center !important;
  vertical-align: middle !important;
}

.table thead th {
  border: none !important;
}

.header-details {
  text-align: center;
  vertical-align: middle;
  padding: 20px;
}

.header-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: left;
  /* height: 200px !important; */
}

.logo {
  text-align: center;
  vertical-align: middle;
}

.signature {
  text-align: right !important;
}

tfoot {
  text-align: right !important;
}

.modal {
  display: none;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 9999;
}

.modal.show {
  display: block;
}
</style>
