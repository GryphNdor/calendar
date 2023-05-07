<script>
  import date from 'date-and-time';

  let now = new Date();

  let todayDate = now.getDate();

  let beginOfTheWeek = date.format(now, 'ddd').toUpperCase();

  while(beginOfTheWeek !== "MON") {
    now = date.addDays(now, -1);
    beginOfTheWeek = date.format(now, 'ddd').toUpperCase();
  }

  let week = [];
  for (let i = 0; i < 7; i++) {
    let today = false;
    if(now.getDate() === todayDate){
      today = true;
    }
    week[i] = {dayOfWeek: date.format(now,'ddd').toUpperCase(), date:
  now.getDate(), today}
    now = date.addDays(now, 1)
  }

</script>


<div class="ml-2 mr-2 mt-10 grid grid-cols-7">
  {#each week as weekday}
  <div class="flex flex-col justify-center items-center"
      class:text-red-500={weekday.today}>
    <h1>{weekday.dayOfWeek}</h1>
    <h1>{weekday.date}</h1>
  </div>
  {/each}
</div>
