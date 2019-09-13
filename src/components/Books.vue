<template>
    <div class="book-wrapper">
        <section class="book-form-section">
            <form class="form" @submit.prevent="addBook">
                <div class="form-field">
                    <label for="book-title" class="book-label">Title:</label>
                    <input type="text" class="book-input" id="book-title" required v-model="book.title">
                </div>
                <div class="form-field">
                    <label for="book-author" class="book-label">Author:</label>
                    <input type="text" class="book-input" id="book-author" required v-model="book.author">
                </div>
                <div class="form-field">
                    <label for="book-pages" class="book-label">Pages:</label>
                    <input type="number" class="book-input" id="book-pages" required min="1" v-model="book.pages">
                </div>
                <div class="form-field">
                    <label for="book-read" class="book-label">Read Yet?</label>
                    <input type="checkbox" class="book-input book-input-checkbox" id="book-read" v-model="book.status">
                </div>
                <button class="form-add-btn" type="submit">Add Book</button>
            </form>
        </section>
        <section class="book-table-section">
            <table class="book-table">
                <thead class="thead">
                    <tr class="thead-row" id="thead-row">
                        <th class="th">Title</th>
                        <th class="th">Author</th>
                        <th class="th table-pages-title">Pages</th>
                        <th class="th">Status (toggle)</th>
                        <th class="th">Delete</th>
                    </tr>
                </thead>
                <tbody class="book-list">
                    <!-- injected books here -->
                    <tr v-for="(value, key) in books" v-bind:key="key">
                        <td>{{ value.title }}</td>
                        <td>{{ value.author }}</td>
                        <td class="table-pages">{{ value.pages }}</td>
                        <td v-if="value.status">
                            <button class="status-btn finished" v-on:click="changeStatus(value, key)">Finished!</button>
                        </td>
                        <td v-else>
                            <button class="status-btn unfinished" v-on:click="changeStatus(value, key)">Not yet</button>
                        </td>
                        <td>
                            <img class="delete-btn" src="../images/trashcan.svg" alt="Trashcan icon" v-on:click="removeBook(key)">
                        </td>
                    </tr>
                </tbody>
            </table>
        </section>
    </div>
</template>

<script>
export default {
    name: "Books",
    data() {
        return {
            book: {
                title: "",
                author: "",
                pages: null,
                status: null
            },
            books: []
        }
    },
    created() {
        this.books = JSON.parse(localStorage.getItem("storedBooks")) || [];
    },
    methods: {
        addBook() {
            this.books.push({title: this.book.title, author: this.book.author, pages: this.book.pages, status: this.book.status});
            this.book.title = "";
            this.book.author = "";
            this.book.pages = null;
            this.book.status = null;

            localStorage.setItem("storedBooks", JSON.stringify(this.books));
        },
        changeStatus(value, key) {
            value.status = !value.status;
            
            localStorage.setItem("storedBooks", JSON.stringify(this.books));
        },
        removeBook(key) {
            this.books.splice(key, 1);

            localStorage.setItem("storedBooks", JSON.stringify(this.books));
        }
    }
}
</script>

<style scoped>

.book-wrapper {
    --light-grey-blue: hsl(203, 19%, 92%);
    --bg-btn-clr: hsla(209, 78%, 51%, 0.992);
    --bg-btn-clr-hover: hsla(209, 80%, 35%, 0.992);
}

/* Book Form Section */

.form {
    width: 960px;
    max-width: 90%;
    margin: 2em auto;
}

.form-field {
    display: flex;
    flex-direction: column;
    margin-top: 1.75em;
}

.form-add-btn {
    margin-top: 1.5em;
    display: block;
    width: 100%;
    padding: .75em;
    cursor: pointer;
    border: none;
    border-radius: 4px;
    background-color: var(--bg-btn-clr);
    color: #fff;
    font-size: 1.1rem;
    outline: none;

    transition:  background-color 210ms ease;
}

.form-add-btn:hover {
    background-color: var(--bg-btn-clr-hover);
}

.book-label {
    margin-bottom: .5em;
    font-weight: 600;
}

.book-input {
    padding-top: .5em;
    padding-bottom: .5em;
    padding-left: .35em;
    font-size: 1rem;
    background-color: var(--light-grey-blue);
    border: none;
    border-radius: 4px;
    font-weight: 400;
}

.book-input-checkbox {
    cursor: pointer;
    width: 1em;
    height: 1em;
}

/* Book List Table */
.book-table {
    width: 960px;
    margin: 6em auto;
    padding: .5em;
    box-shadow: 0 6px 14px rgba(0, 0, 0, .2);
    border-radius: 4px;
    table-layout: fixed;
    border-collapse: collapse;
}

th,
td {
    padding: 1em;
}

th {
    text-align: left;
}

.table-pages-title {
    text-align: center;
}

.table-pages {
    text-align: right;
    padding-right: 4.35em;
    font-feature-settings: "tnum";
}

#thead-row {
    background-color: #fafafa;
}

tr:nth-child(odd) {
    background-color: var(--light-grey-blue);
}

tr:nth-child(even) {
    background-color: hsl(204, 24%, 100%);
}

.status-btn {
    padding: .5em 1.25em;
    border: none;
    border-radius: 4px;
    outline: none;
    cursor: pointer;
}

.finished {
    background-color: hsl(120, 75%, 74%);
    color: #000;
    transition: background-color 200ms ease,
                color 200ms ease;
}

.finished:hover {
    background-color: hsl(120, 75%, 30%);
    color: #fff;
}

.unfinished {
    background-color: hsl(12, 100%, 68%);
    color: #000;
    transition: background-color 200ms ease,
                color 200ms ease;
}

.unfinished:hover {
    background-color: hsl(12, 100%, 38%);
    color: #fff;
}

.delete-btn {
    width: 35px;
    cursor: pointer;
    transition: opacity 150ms ease;
}

.delete-btn:hover {
    opacity: .7;
}

@media screen and (max-width: 66.56em) {
    .book-table {
        width: 90%;
    }
}

@media screen and (max-width: 47em) {
    .book-table {
        font-size: .75rem;
    }

    th,
    td {
        padding: .75em;
    }

    .table-pages {
        text-align: right;
        padding-right: 3.25em;
    }

    .status-btn {
        padding: .2em .5em;
    }
}

@media screen and (max-width: 25em) {
    .table-pages {
        text-align: right;
        padding-right: 1.25em;
    }
}

</style>
