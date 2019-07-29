<template>
    <div>
        <section class="book-form-section">
            <form class="form" @submit.prevent="addBook">
                <div class="form-field">
                    <label for="book-title" class="book-label">Title:</label>
                    <input type="text" class="book-input" id="book-title" v-model="book.title">
                </div>
                <div class="form-field">
                    <label for="book-author" class="book-label">Author:</label>
                    <input type="text" class="book-input" id="book-author" v-model="book.author">
                </div>
                <div class="form-field">
                    <label for="book-pages" class="book-label">Pages:</label>
                    <input type="text" class="book-input" id="book-pages" v-model="book.pages">
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
                        <th class="th">Pages</th>
                        <th class="th">Status</th>
                        <th class="th">Delete</th>
                    </tr>
                </thead>
                <tbody class="book-list">
                    <!-- injected books here -->
                    <tr v-for="(value, key) in books" v-bind:key="key">
                        <td>{{ value.title }}</td>
                        <td>{{ value.author }}</td>
                        <td>{{ value.pages }}</td>
                        <td>{{ value.status }}</td>
                        <td><img class="delete-btn" src="../images/trashcan.svg" alt="Trashcan icon"></td>
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
                status: false
            },
            books: []
        }
    },
    methods: {
        addBook() {
            this.books.push({title: this.book.title, author: this.book.author, pages: this.book.pages, status: this.book.status});
            this.book.title = "";
            this.book.author = "";
            this.book.pages = null;
            this.book.status = false;
        }
    }
}
</script>

<style scoped>

/* Book Form Section */
.form {
    width: 960px;
    max-width: 90%;
    margin: 2em auto;
}

.form-field {
    display: flex;
    flex-direction: column;
    margin-top: 1em;
    margin-bottom: 1em;
}

.form-add-btn {
    display: block;
    width: 100%;
    padding: .75em;
    cursor: pointer;
    border: none;
    border-radius: 4px;
    background-color: #2286e4fd;
    color: #fff;
    font-size: 1.1rem;
    outline: none;
}

.book-label {
    margin-bottom: .5em;
    font-weight: bolder;
}

.book-input {
    padding-top: .25em;
    padding-bottom: .25em;
    font-size: 1.1rem;
}

.book-input-checkbox {
    cursor: pointer;
    width: 1em;
    height: 1em;
}

/* Book List Table */
.book-table {
    width: 960px;

    margin: 0 auto;
    margin-top: 2em;
    margin-bottom: 3em;
    padding: .5em;
    border-top: 1px solid #ccc;
    border-bottom: 1px solid #ccc;
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

#thead-row {
    background-color: #fbfbfb;
}

tr:nth-child(odd) {
    background-color: #ddd;
}

.delete-btn {
    width: 40px;
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

}

</style>
