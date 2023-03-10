# -Python--
const { spawn } = require('child_process');

// Запускаем скрипт python
const pythonProcess = spawn('python', ['script.py']);

// Получаем вывод из скрипта python
pythonProcess.stdout.on('data', (data) => {
  console.log(`Python script output: ${data}`);
});

// Обработка ошибок
pythonProcess.on('error', (err) => {
  console.error(`Failed to start Python script: ${err}`);
});

pythonProcess.on('exit', (code, signal) => {
  if (signal) {
    console.log(`Python script was terminated by ${signal}`);
  } else if (code !== 0) {
    console.error(`Python script exited with code ${code}`);
  } else {
    console.log('Python script finished successfully');
  }
});
