<template>
    <div>
      <span class="date">{{ currentDateTime.split(' ')[0] }}</span>
      <span class="time">{{ currentDateTime.split(' ')[1] }}</span>
    </div>
  </template>
  
  <script>
  import { format } from 'date-fns';
  
  export default {
    name: 'CurrentDateTime',
    data() {
      return {
        currentDateTime: format(new Date(), 'yyyy-MM-dd HH:mm:ss')
      };
    }
  }
  </script>
  
  <style>
  .date {
    font-size: 2em;
    color: #3498db; /* Blue color for date */
  }
  .time {
    font-size: 2em;
    color: #e74c3c; /* Red color for time */
  }
  </style>