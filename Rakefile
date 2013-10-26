desc "Reset all code after an iteration"
task :reset do
  `git reset --hard`
  `git clean -fxd .`
end

DEFAULT_MINUTES = 5

desc "Run an auto-reset timer constraint"
task :timer, :minutes do |t, args|
  while true
    minutes = args[:minutes] || DEFAULT_MINUTES
    puts "Waiting #{minutes} minutes..."
    while minutes > 0
      sleep(60)
      minutes -= 1
      text = (minutes == 1) ? "minute" : "minutes"
      puts "  #{minutes} #{text} left"
      `say "#{minutes} #{text}"`
    end
    `say "Reset in 10 seconds"`
    puts "Resetting..."
    Rake::Task[:reset].invoke
  end
end