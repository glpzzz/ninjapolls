<script>

    import Button from '../shared/Button.svelte';

    let fields = {
        question: '',
        answerA: '',
        answerB: ''
    }
    let errors = {
        question: '',
        answerA: '',
        answerB: ''
    }
    let valid = false;

    const submitHandler = () => {
        valid = true;
        // validate question
        if (fields.question.trim().length < 5) {
            valid = false;
            errors.question = 'Question must be at least 5 chars long.';
        } else {
            errors.question = '';
        }

        // validate answer A
        if (fields.answerA.trim().length < 1) {
            valid = false;
            errors.answerA = 'Answer A can\'t be empty';
        } else {
            errors.answerA = '';
        }

        // validate answer B
        if (fields.answerB.trim().length < 1) {
            valid = false;
            errors.answerB = 'Answer B can\'t be empty';
        } else {
            errors.answerB = '';
        }

        if (valid) {
            console.log('valid', fields);
        } else {
            console.log(errors);
        }

    }
</script>

<form on:submit|preventDefault={submitHandler}>

    <div class="form-field">
        <label for="question">Poll Question:</label>
        <input type="text" id="question" bind:value={fields.question}>
        <p class="errors">{errors.question}</p>
    </div>

    <div class="form-field">
        <label for="answer-a">Answer A:</label>
        <input type="text" id="answer-a" bind:value={fields.answerA}>
        <p class="errors">{errors.answerA}</p>
    </div>

    <div class="form-field">
        <label for="answer-b">Answer B:</label>
        <input type="text" id="answer-b" bind:value={fields.answerB}>
        <p class="errors">{errors.answerB}</p>
    </div>

    <Button type="secondary" flat="{true}">Add Poll</Button>

</form>

<style>
    form {
        width: 400px;
        margin: 0 auto;
        text-align: center;
    }

    .form-field {
        margin: 18px auto;

    }

    input[type=text] {
        width: 100%;
        border-radius: 6px;
    }

    label {
        margin: 10px auto;
        text-align: left;
    }

    .errors{
        font-size: 85%;
        color: #d91b42;
        font-weight: bold;

    }

</style>
