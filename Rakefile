require "bundler"
Bundler.require(:default)

task "build" do
  emojis = Emoji.all.each_with_object({}) do |emoji, hash|
    emoji.aliases.map do |emoji_alias|
      emoji_raw = emoji.raw.nil? ? ":#{emoji_alias}:" : emoji.raw + " "
      hash[emoji_alias] = emoji_raw
    end
  end

  emojify = <<-EOF
  #!/usr/bin/env ruby

  EMOJIS = #{emojis}

  def emojify(line)
    line.gsub(/:([\\w+-]+):/) do |match|
      EMOJIS[$1]
    end
  end

  ARGF.read.each_line do |line|
    puts emojify(line)
  end
  EOF

  File.open("./bin/emojify", "w") do |file|
    file.write(emojify)
  end
end
