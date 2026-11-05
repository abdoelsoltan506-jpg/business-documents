# business-documents
<!doctype html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">

<title>مركز مستندات الأعمال</title>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
:root {
    --navy: #17324d;
    --blue: #2563eb;
    --bg: #f4f7fb;
    --white: #ffffff;
    --text: #1f2937;
    --muted: #6b7280;
    --line: #dbe3ee;
    --green: #16845b;
    --red: #b42318;
    --orange: #a76500;
}

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    background: var(--bg);
    color: var(--text);
    font-family: Tahoma, Arial, sans-serif;
}

header {
    background: var(--navy);
    color: white;
    padding: 20px;
}

.header-inner {
    max-width: 1200px;
    margin: auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 15px;
}

header h1 {
    margin: 0;
    font-size: 1.4rem;
}

header p {
    margin: 6px 0 0;
    color: #c9d7e7;
    font-size: 0.85rem;
}

#connection {
    font-size: 0.8rem;
    color: #b9f6d3;
}

.container {
    max-width: 1200px;
    margin: auto;
    padding: 20px 14px;
}

.panel {
    background: white;
    border: 1px solid var(--line);
    border-radius: 14px;
    padding: 17px;
    margin-bottom: 18px;
    box-shadow: 0 3px 14px #17324d12;
}

.panel h2 {
    color: var(--navy);
    font-size: 1.05rem;
    margin: 0 0 14px;
}

.form-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 11px;
}

.full-width {
    grid-column: span 2;
}

label {
    display: block;
    color: var(--muted);
    font-size: 0.73rem;
    margin-bottom: 5px;
}

input,
select,
textarea,
button {
    font: inherit;
}

input,
select,
textarea {
    width: 100%;
    padding: 10px;
    border: 1px solid var(--line);
    border-radius: 8px;
    background: white;
    color: var(--text);
}

textarea {
    min-height: 70px;
    resize: vertical;
}

button {
    cursor: pointer;
}

.primary-button,
.secondary-button {
    border: 0;
    border-radius: 8px;
    padding: 10px 18px;
    font-weight: bold;
}

.primary-button {
    background: var(--blue);
    color: white;
}

.secondary-button {
    background: #edf2f7;
    color: var(--navy);
}

.actions {
    display: flex;
    gap: 9px;
    align-items: center;
    flex-wrap: wrap;
    margin-top: 14px;
}

.message {
    font-size: 0.8rem;
}

.cards {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 15px;
}

.card {
    background: white;
    border: 1px solid var(--line);
    border-radius: 14px;
    padding: 16px;
    box-shadow: 0 4px 15px #17324d12;
}

.card-header {
    display: flex;
    justify-content: space-between;
    gap: 10px;
}

.document-type {
    color: var(--navy);
    font-weight: bold;
    font-size: 1.05rem;
}

.document-number {
    color: var(--muted);
    font-size: 0.75rem;
    margin-top: 5px;
}

.status {
    background: #e8f5ef;
    color: var(--green);
    border-radius: 20px;
    padding: 5px 9px;
    height: fit-content;
    font-size: 0.72rem;
    white-space: nowrap;
}

.status-review {
    background: #fff4dd;
    color: var(--orange);
}

.status-closed {
    background: #fbe9e7;
    color: var(--red);
}

.card-data {
    border-top: 1px solid var(--line);
    margin-top: 14px;
    padding-top: 12px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 11px;
    font-size: 0.82rem;
}

.card-data span,
.details span {
    display: block;
    color: var(--muted);
    font-size: 0.7rem;
    margin-bottom: 3px;
}

.amount {
    color: var(--blue);
    font-weight: bold;
}

.details-button {
    width: 100%;
    border: 0;
    border-radius: 8px;
    padding: 10px;
    margin-top: 14px;
    background: #edf3ff;
    color: #1d4ed8;
}

.empty {
    background: white;
    border: 1px dashed var(--line);
    border-radius: 14px;
    padding: 35px;
    text-align: center;
    color: var(--muted);
    grid-column: 1 / -1;
}

.pagination {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    margin-top: 18px;
}

.pagination button {
    border: 1px solid var(--line);
    background: white;
    border-radius: 7px;
    padding: 8px 15px;
}

.pagination button:disabled {
    opacity: 0.45;
    cursor: not-allowed;
}

.login-screen {
    position: fixed;
    inset: 0;
    z-index: 10;
    background: #0b1726dd;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
}

.login-box {
    background: white;
    width: min(390px, 100%);
    border-radius: 15px;
    padding: 25px;
}

.login-box h2 {
    color: var(--navy);
    margin-top: 0;
}

.login-box input {
    margin-bottom: 12px;
}

.hidden {
    display: none !important;
}

dialog {
    border: 0;
    border-radius: 15px;
    width: min(650px, 95%);
    padding: 0;
}

dialog::backdrop {
    background: #0b1726aa;
}

.modal {
    padding: 22px;
}

.modal-header {
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid var(--line);
    padding-bottom: 12px;
}

.close-button {
    border: 0;
    border-radius: 7px;
    padding: 7px 11px;
}

.details {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
    margin: 18px 0;
}

.items {
    border-top: 1px solid var(--line);
    padding-top: 14px;
}

.item {
    display: flex;
    justify-content: space-between;
    padding: 9px 0;
    border-bottom: 1px solid #edf1f6;
}

@media (max-width: 760px) {
    .form-grid {
        grid-template-columns: 1fr 1fr;
    }

    .full-width {
        grid-column: span 2;
    }
}

@media (max-width: 500px) {
    .header-inner {
        display: block;
    }

    .form-grid {
        grid-template-columns: 1fr;
    }

    .full-width {
        grid-column: auto;
    }

    .details {
        grid-template-columns: 1fr;
    }
}
</style>
</head>

<body>

<!-- نافذة تسجيل الدخول -->
<div id="login-screen" class="login-screen">
    <div class="login-box">
        <h2>دخول مركز المستندات</h2>

        <label>البريد الإلكتروني</label>
        <input id="login-email" type="email" placeholder="name@gmail.com">

        <label>كلمة المرور</label>
        <input id="login-password" type="password">

        <button
            class="primary-button"
            style="width:100%;"
            onclick="loginUser()">
            دخول
        </button>

        <p id="login-message" class="message"></p>
    </div>
</div>

<header>
    <div class="header-inner">
        <div>
            <h1>مركز مستندات الأعمال</h1>
            <p>إدارة وأرشفة عمليات الشركة في بطاقات واضحة</p>
        </div>

        <div>
            <span id="connection">جاري الاتصال...</span>
              

            <button
                id="logout-button"
                class="secondary-button hidden"
                onclick="logoutUser()">
                خروج
            </button>
        </div>
    </div>
</header>

<main class="container">

<!-- إدخال مستند -->
<section class="panel">
    <h2>إدخال مستند جديد</h2>

    <div class="form-grid">

        <div>
            <label>نوع المستند</label>
            <select id="document-type">
                <option>فاتورة</option>
                <option>عرض سعر</option>
                <option>خطاب ضمان</option>
                <option>أمر إسناد</option>
                <option>شيك</option>
                <option>عقد</option>
                <option>وارد</option>
                <option>صادر</option>
                <option>تقرير</option>
            </select>
        </div>

        <div>
            <label>الرقم الداخلي</label>
            <input id="document-number" placeholder="INV-001">
        </div>

        <div>
            <label>العميل أو الجهة</label>
            <input id="entity-name">
        </div>

        <div>
            <label>تاريخ المستند - تلقائي</label>
            <input id="document-date" type="date" readonly>
        </div>

        <div>
            <label>الحالة</label>
            <select id="document-status">
                <option>مفتوح</option>
                <option>قيد المراجعة</option>
                <option>ساري</option>
                <option>مغلق</option>
                <option>ملغي</option>
            </select>
        </div>

        <div>
            <label>القيمة</label>
            <input id="amount" type="number" step="0.01">
        </div>

        <div>
            <label>من / بداية الفترة</label>
            <input id="period-from">
        </div>

        <div>
            <label>إلى / نهاية الفترة</label>
            <input id="period-to">
        </div>

        <div class="full-width">
            <label>البيان أو الصنف</label>
            <input id="item-name">
        </div>

        <div>
            <label>الكمية</label>
            <input id="item-quantity" type="number" value="1">
        </div>

        <div>
            <label>سعر الوحدة</label>
            <input id="item-price" type="number" step="0.01" value="0">
        </div>

        <div class="full-width">
            <label>رابط المصدر أو المرفق</label>
            <input id="source-url" type="url">
        </div>

        <div class="full-width">
            <label>ملاحظات</label>
            <textarea id="notes"></textarea>
        </div>

    </div>

    <div class="actions">
        <button class="primary-button" onclick="saveDocument()">
            حفظ المستند
        </button>

        <button class="secondary-button" onclick="clearForm()">
            مسح الخانات
        </button>

        <span id="form-message" class="message"></span>
    </div>
</section>

<!-- الفلاتر -->
<section class="panel">
    <h2>البحث والفلترة</h2>

    <div class="form-grid">

        <div class="full-width">
            <label>بحث</label>
            <input
                id="search-text"
                placeholder="رقم المستند أو الجهة أو الملاحظات">
        </div>

        <div>
            <label>نوع المستند</label>
            <select id="filter-type">
                <option value="">كل الأنواع</option>
            </select>
        </div>

        <div>
            <label>الحالة</label>
            <select id="filter-status">
                <option value="">كل الحالات</option>
            </select>
        </div>

        <div>
            <label>اليوم</label>
            <select id="filter-day">
                <option value="">كل الأيام</option>
            </select>
        </div>

        <div>
            <label>الشهر</label>
            <select id="filter-month">
                <option value="">كل الشهور</option>
            </select>
        </div>

        <div>
            <label>السنة</label>
            <select id="filter-year">
                <option value="">كل السنوات</option>
            </select>
        </div>

        <div>
            <label>بطاقات الصفحة</label>
            <select id="page-size">
                <option value="12">12</option>
                <option value="24">24</option>
                <option value="48">48</option>
            </select>
        </div>

    </div>

    <div class="actions">

        <button class="primary-button" onclick="applyFilters()">
            تطبيق الفلترة
        </button>

        <button class="secondary-button" onclick="showAllDocuments()">
            عرض الكل
        </button>

        <span id="filter-message" class="message"></span>
    </div>
</section>

<div style="display:flex;justify-content:space-between;">
    <h2 style="color:var(--navy);">
        المستندات
    </h2>

    <span id="document-count"></span>
</div>

<section id="cards" class="cards">
    <div class="empty">جاري التحميل...</div>
</section>

<div class="pagination">
    <button id="previous-button" onclick="changePage(-1)">
        السابق
    </button>

    <span id="page-info"></span>

    <button id="next-button" onclick="changePage(1)">
        التالي
    </button>
</div>

</main>

<!-- نافذة التفاصيل -->
<dialog id="details-dialog">
    <div class="modal">

        <div class="modal-header">
            <h2 id="modal-title"></h2>

            <button
                class="close-button"
                onclick="closeDetails()">
                إغلاق
            </button>
        </div>

        <div id="modal-body"></div>
    </div>
</dialog>

<script>

/* بيانات مشروع Supabase الجديد فقط */
const SUPABASE_URL =
    "https://jhnggomihzdtexiwtwwb.supabase.co";

const SUPABASE_ANON_KEY =
    "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Impobmdnb21paHpkdGV4aXd0d3diIiwicm9sZSI6ImFub24iLCJpYXQiOjE3OTM4OTYwOTMsImV4cCI6MjEwOTQ3MjA5M30.TV0_1-wrXnQJG29HUZiEJQKxJcQdW3AyjITKhSgn0JQ";


const db = supabase.createClient(
    SUPABASE_URL,
    SUPABASE_ANON_KEY
);

let currentPage = 0;
let totalDocuments = 0;
let currentDocuments = [];

const $ = id => document.getElementById(id);

function escapeHtml(value) {
    return String(value ?? "").replace(
        /[&<>"']/g,
        character => ({
            "&": "&amp;",
            "<": "&lt;",
            ">": "&gt;",
            '"': "&quot;",
            "'": "&#39;"
        }[character])
    );
}

function todayDate() {
    return new Date().toISOString().slice(0, 10);
}

$("document-date").value = todayDate();

async function loginUser() {
    const emailInput =
        document.getElementById("login-email");

    const passwordInput =
        document.getElementById("login-password");

    const message =
        document.getElementById("login-message");

    const email =
        emailInput.value.trim();

    const password =
        passwordInput.value;

    if (!email || !password) {
        message.style.color = "#b42318";
        message.textContent =
            "اكتب البريد الإلكتروني وكلمة المرور";
        return;
    }

    message.style.color = "#a76500";
    message.textContent =
        "جاري التحقق من البيانات...";

    const result =
        await db.auth.signInWithPassword({
            email: email,
            password: password
        });

    if (result.error) {
        console.error(result.error);

        message.style.color = "#b42318";
        message.textContent =
            "فشل الدخول: " + result.error.message;

        return;
    }

    message.style.color = "#16845b";
    message.textContent =
        "تم الدخول بنجاح";

    document
        .getElementById("login-screen")
        .classList.add("hidden");

    document
        .getElementById("logout-button")
        .classList.remove("hidden");

    await loadFilters();
    await loadDocuments();
}

/* تسجيل الخروج */
async function logoutUser() {
    await db.auth.signOut();
    location.reload();
}

/* تجهيز استعلام الفلترة */
function buildQuery() {
    let query = db
        .from("business_documents")
        .select("*", { count: "exact" })
        .order("document_date", { ascending: false })
        .order("created_at", { ascending: false });

    const search =
        $("search-text").value.trim();

    const type =
        $("filter-type").value;

    const status =
        $("filter-status").value;

    const day =
        $("filter-day").value;

    const month =
        $("filter-month").value;

    const year =
        $("filter-year").value;

    if (search) {
        query = query.or(
            `document_number.ilike.%${search}%,
             entity_name.ilike.%${search}%,
             notes.ilike.%${search}%`
        );
    }

    if (type) {
        query = query.eq("document_type", type);
    }

    if (status) {
        query = query.eq("status", status);
    }

    if (day) {
        query = query.eq("document_day", Number(day));
    }

    if (month) {
        query = query.eq("document_month", Number(month));
    }

    if (year) {
        query = query.eq("document_year", Number(year));
    }

    return query;
}

/* تحميل صفحة واحدة فقط */
async function loadDocuments() {
    const pageSize =
        Number($("page-size").value);

    const start =
        currentPage * pageSize;

    const end =
        start + pageSize - 1;

    const result =
        await buildQuery().range(start, end);

    if (result.error) {
        $("cards").innerHTML =
            `<div class="empty">
                ${escapeHtml(result.error.message)}
             </div>`;
        return;
    }

    currentDocuments =
        result.data || [];

    totalDocuments =
        result.count || 0;

    renderCards();

    const totalPages =
        Math.ceil(totalDocuments / pageSize);

    $("document-count").textContent =
        `${totalDocuments} مستند إجمالًا`;

    $("page-info").textContent =
        totalPages
            ? `صفحة ${currentPage + 1} من ${totalPages}`
            : "لا توجد نتائج";

    $("previous-button").disabled =
        currentPage === 0;

    $("next-button").disabled =
        (currentPage + 1) * pageSize >= totalDocuments;
}

/* تحميل قيم الفلاتر */
async function loadFilters() {
    const result = await db
        .from("business_documents")
        .select("document_type,status,document_date")
        .limit(1000);

    if (result.error) {
        return;
    }

    const types = [
        ...new Set(
            result.data
                .map(row => row.document_type)
                .filter(Boolean)
        )
    ].sort();

    const statuses = [
        ...new Set(
            result.data
                .map(row => row.status)
                .filter(Boolean)
        )
    ].sort();

    const years = [
        ...new Set(
            result.data
                .map(row => row.document_date?.slice(0, 4))
                .filter(Boolean)
        )
    ].sort().reverse();

    $("filter-type").innerHTML =
        `<option value="">كل الأنواع</option>` +
        types.map(type =>
            `<option value="${escapeHtml(type)}">
                ${escapeHtml(type)}
             </option>`
        ).join("");

    $("filter-status").innerHTML =
        `<option value="">كل الحالات</option>` +
        statuses.map(status =>
            `<option value="${escapeHtml(status)}">
                ${escapeHtml(status)}
             </option>`
        ).join("");

    $("filter-year").innerHTML =
        `<option value="">كل السنوات</option>` +
        years.map(year =>
            `<option value="${year}">${year}</option>`
        ).join("");

    $("filter-month").innerHTML =
        `<option value="">كل الشهور</option>` +
        Array.from({ length: 12 }, (_, index) => {
            const month =
                String(index + 1).padStart(2, "0");

            return `<option value="${month}">
                        ${month}
                    </option>`;
        }).join("");

    $("filter-day").innerHTML =
        `<option value="">كل الأيام</option>` +
        Array.from({ length: 31 }, (_, index) => {
            const day =
                String(index + 1).padStart(2, "0");

            return `<option value="${day}">
                        ${day}
                    </option>`;
        }).join("");

    $("connection").textContent =
        "متصل بالمستندات";
}

/* عرض البطاقات */
function renderCards() {
    if (!currentDocuments.length) {
        $("cards").innerHTML =
            `<div class="empty">
                لا توجد مستندات مطابقة.
             </div>`;
        return;
    }

    $("cards").innerHTML =
        currentDocuments.map(document => {

            const statusClass =
                document.status === "قيد المراجعة"
                    ? "status-review"
                    : document.status === "مغلق" ||
                      document.status === "ملغي"
                        ? "status-closed"
                        : "";

            const createdTime =
                document.created_at
                    ? new Date(
                        document.created_at
                      ).toLocaleString("ar-EG")
                    : "—";

            const itemsCount =
                Array.isArray(document.items)
                    ? document.items.length
                    : 0;

            return `
                <article class="card">

                    <div class="card-header">
                        <div>
                            <div class="document-type">
                                ${escapeHtml(
                                    document.document_type
                                )}
                            </div>

                            <div class="document-number">
                                الرقم:
                                ${escapeHtml(
                                    document.document_number || "—"
                                )}
                            </div>
                        </div>

                        <span class="status ${statusClass}">
                            ${escapeHtml(document.status)}
                        </span>
                    </div>

                    <div class="card-data">

                        <div>
                            <span>الجهة</span>
                            ${escapeHtml(document.entity_name)}
                        </div>

                        <div>
                            <span>تاريخ المستند</span>
                            ${escapeHtml(document.document_date)}
                        </div>

                        <div>
                            <span>وقت التسجيل من Supabase</span>
                            ${escapeHtml(createdTime)}
                        </div>

                        <div>
                            <span>القيمة</span>
                            <b class="amount">
                                ${
                                    document.amount == null
                                        ? "—"
                                        : Number(
                                            document.amount
                                          ).toLocaleString(
                                            "ar-EG",
                                            {
                                                minimumFractionDigits: 2
                                            }
                                          )
                                }
                            </b>
                        </div>

                        <div>
                            <span>عدد البنود</span>
                            ${itemsCount}
                        </div>

                    </div>

                    <button
                        class="details-button"
                        onclick="openDetails('${document.id}')">
                        فتح التفاصيل
                    </button>

                </article>
            `;
        }).join("");
}

/* حفظ مستند */
async function saveDocument() {
    const entity =
        $("entity-name").value.trim();

    const message =
        $("form-message");

    if (!entity) {
        message.style.color = "var(--red)";
        message.textContent =
            "اكتب اسم الجهة أولًا";
        return;
    }

    const quantity =
        Number($("item-quantity").value || 0);

    const price =
        Number($("item-price").value || 0);

    const itemName =
        $("item-name").value.trim();

    const amount =
        $("amount").value === ""
            ? quantity * price
            : Number($("amount").value);

    const data = {
        document_type:
            $("document-type").value,

        document_number:
            $("document-number").value.trim() || null,

        entity_name:
            entity,

        status:
            $("document-status").value,

        amount,

        period_from:
            $("period-from").value.trim() || null,

        period_to:
            $("period-to").value.trim() || null,

        source_url:
            $("source-url").value.trim() || null,

        notes:
            $("notes").value.trim() || null,

        items: itemName
            ? [
                {
                    name: itemName,
                    quantity,
                    price,
                    total: quantity * price
                }
            ]
            : []

        /*
          لا نرسل document_date هنا.
          Supabase يضع التاريخ الحالي تلقائيًا.
          وcreated_at يضع التاريخ والوقت تلقائيًا.
        */
    };

    message.style.color = "var(--orange)";
    message.textContent = "جاري الحفظ...";

    const result =
        await db
            .from("business_documents")
            .insert(data);

    if (result.error) {
        message.style.color = "var(--red)";
        message.textContent =
            "فشل الحفظ: " + result.error.message;
        return;
    }

    message.style.color = "var(--green)";
    message.textContent =
        "تم حفظ المستند بنجاح";

    clearForm();

    await loadFilters();
    currentPage = 0;
    await loadDocuments();
}

/* مسح النموذج */
function clearForm() {
    [
        "document-number",
        "entity-name",
        "period-from",
        "period-to",
        "item-name",
        "source-url",
        "notes"
    ].forEach(id => {
        $(id).value = "";
    });

    $("amount").value = "";
    $("item-quantity").value = 1;
    $("item-price").value = 0;
    $("document-date").value = todayDate();
}

/* فتح التفاصيل */
function openDetails(id) {
    const document =
        currentDocuments.find(
            row => String(row.id) === String(id)
        );

    if (!document) {
        return;
    }

    $("modal-title").textContent =
        `${document.document_type} — ${
            document.document_number || "بدون رقم"
        }`;

    const items =
        Array.isArray(document.items)
            ? document.items
            : [];

    $("modal-body").innerHTML = `
        <div class="details">

            <div>
                <span>الجهة</span>
                ${escapeHtml(document.entity_name)}
            </div>

            <div>
                <span>تاريخ المستند</span>
                ${escapeHtml(document.document_date)}
            </div>

            <div>
                <span>وقت التسجيل</span>
                ${
                    document.created_at
                        ? new Date(
                            document.created_at
                          ).toLocaleString("ar-EG")
                        : "—"
                }
            </div>

            <div>
                <span>الحالة</span>
                ${escapeHtml(document.status)}
            </div>

            <div>
                <span>القيمة</span>
                ${
                    document.amount == null
                        ? "—"
                        : Number(
                            document.amount
                          ).toLocaleString(
                            "ar-EG",
                            {
                                minimumFractionDigits: 2
                            }
                          )
                }
            </div>

            <div>
                <span>الفترة</span>
                ${escapeHtml(
                    [
                        document.period_from,
                        document.period_to
                    ]
                    .filter(Boolean)
                    .join(" — ") || "—"
                )}
            </div>

            <div>
                <span>المصدر</span>
                ${
                    document.source_url
                        ? `
                            <a
                                href="${escapeHtml(
                                    document.source_url
                                )}"
                                target="_blank">
                                فتح الرابط
                            </a>
                          `
                        : "—"
                }
            </div>

        </div>

        <div class="items">
            <b>الأصناف</b>

            ${
                items.length
                    ? items.map(item => `
                        <div class="item">
                            <span>
                                ${escapeHtml(item.name)}
                                ×
                                ${escapeHtml(item.quantity)}
                            </span>

                            <b>
                                ${escapeHtml(item.total)}
                            </b>
                        </div>
                    `).join("")
                    : "<p>لا توجد أصناف مسجلة.</p>"
            }
        </div>

        <p style="color:var(--muted);">
            ${escapeHtml(
                document.notes || "لا توجد ملاحظات"
            )}
        </p>
    `;

    $("details-dialog").showModal();
}

function closeDetails() {
    $("details-dialog").close();
}

/* تطبيق الفلاتر */
function applyFilters() {
    currentPage = 0;

    $("filter-message").textContent =
        "تم تطبيق الفلترة";

    loadDocuments();
}

/* عرض كل المستندات مع بقاء التقسيم */
function showAllDocuments() {
    $("search-text").value = "";
    $("filter-type").value = "";
    $("filter-status").value = "";
    $("filter-day").value = "";
    $("filter-month").value = "";
    $("filter-year").value = "";

    currentPage = 0;

    $("filter-message").textContent =
        "تم عرض كل المستندات";

    loadDocuments();
}

/* تغيير الصفحة */
function changePage(number) {
    currentPage =
        Math.max(0, currentPage + number);

    loadDocuments();
}

/* تفعيل البحث وتغيير حجم الصفحة */
$("search-text").addEventListener(
    "input",
    () => {
        currentPage = 0;
        loadDocuments();
    }
);

$("page-size").addEventListener(
    "change",
    () => {
        currentPage = 0;
        loadDocuments();
    }
);

/* بدء النظام */
async function startApplication() {
    const session =
        await db.auth.getSession();

    if (session.data.session) {
        $("login-screen").classList.add("hidden");
        $("logout-button").classList.remove("hidden");

        await loadFilters();
        await loadDocuments();
    } else {
        $("connection").textContent =
            "يجب تسجيل الدخول";
    }
}

startApplication();

</script>

</body>
</html>
