<h1>Учет расходов</h1>

<form on:submit|preventDefault={addExpense}>
 <label for="name">Название:</label>
 <input type="text" id="name" bind:value={newName} />
 <label for="amount">Сумма:</label>
 <input type="text" id="amount" bind:value={newAmount} />
 <button type="submit">Добавить</button>
</form>

<table>
 <thead>
  <tr>
   <th>Название</th>
   <th>Сумма</th>
   <th>Действия</th>
  </tr>
 </thead>
 <tbody>
  {#each expenses as expense, i}
   <tr>
    <td><div>{expense.name}</div> </td>
    <td><div>{expense.amount}</div> </td>
    <td><button on:click={() => deleteExpense(i)}>Удалить</button></td>
   </tr>
  {/each}
 </tbody>
</table>

<script>
 let expenses = [];

 let newName = '';
 let newAmount = '';

 function addExpense() {
  const obj = {
   name: newName,
   amount: parseInt(newAmount),
  };
  expenses.push(obj);
  expenses = expenses;
  newName = '';
  newAmount = '';
 }

 function deleteExpense(index) {
  expenses.splice(index, 1);
  expenses = expenses;
 }
</script>

<style>
 label {
  display: block;
  margin-bottom: 10px;
 }
 input[type='text'] {
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-right: 10px;
  width: 150px;
 }
 table {
  margin-top: 20px;
  border-collapse: collapse;
  width: 100%;
 }
 th,
 td {
  border: 1px solid #ccc;
  padding: 8px;
  text-align: left;
 }
 th {
  background-color: #eee;
 }
 button {
  padding: 5px 10px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
 }
 h1 {
  font-size: 24px;
  margin-bottom: 20px;
 }
</style>