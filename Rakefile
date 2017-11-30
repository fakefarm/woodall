require 'stringex'

desc "Create a new post"
task :post, :title do |t, args|
  mkdir_p './content/posts'
  args.with_defaults(:title=> 'New Post')
  title = args.title
  filename = "./content/posts/#{Time.now.strftime('%Y-%m-%d')}-#{title.to_url}.md"

  if File.exist?(filename)
    abort('rake aborted') if ask("#{filename} already exists. Want to overwrite?", ['y', 'n']) == 'n'
  end

  puts "Building: #{filename}"
  open(filename, 'w') do |post|
    post.puts '---'
    post.puts "title: #{title}"
    post.puts "description: #{title}"
    post.puts "created_at: #{Time.now}"
    post.puts "last_updated: #{Time.now}"
    post.puts 'kind: article'
    post.puts 'published: false'
    post.puts "---\n\n"
  end
end


# nanoc --env=[prod]
