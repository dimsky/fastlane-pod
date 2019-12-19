skip_docs

lane :release_pod do |options|
  target_version = options[:version]
  target_msg = options[:msg]
  default_pod_repo_url = "https://cdn.cocoapods.org/"

  # 获取当前git 用户名
  gitUserName = sh('git config user.name').chomp

  # 搜索 podspec 文件名
  spec_path = ""
  
  Dir["../*.podspec", "./*.podspec"].each{|x|
      spec_path = File.basename(x)
      break
  }

  if spec_path == "" 
    UI.user_error!("PodName.podspec not found")
  end

  # git pull
  git_pull
  # 确认是 master 分支
  ensure_git_branch

  # 验证 spec 文件
  pod_lib_lint(allow_warnings: true, use_libraries: false)

  # 修改 spec 为即将发布的版本
  version_bump_podspec(path: spec_path, version_number: target_version)
  # 提交代码到远程仓库
  git_add(path: '.')
  begin
   git_commit(path: '.', message: "[#{gitUserName}] release pod with version=#{target_version} msg: #{target_msg}")
  rescue => ex
   UI.error(ex)
  end
  
  push_to_git_remote
  # 检查对于 tag 是否已经存在
  if git_tag_exists(tag: target_version)
      # 删除对应 tag
      remove_git_tag(tag: target_version)
  end
  # 添加 tag
  add_git_tag(tag: target_version)
  # 提交 tag
  push_git_tags
  pod_push(path: spec_path, allow_warnings: true, use_libraries: false)
end



lane :pod_lint do 
pod_lib_lint(allow_warnings: true, use_libraries: false)

end

lane :test do
 podSpecFileName = ""
 Dir["../*.podspec", "./*.podspec"].each{|x|
    podSpecFileName = File.basename(x)
    break
 }
  if podSpecFileName == "" 
    UI.user_error!("My error message")
  end

  puts "finded #{podSpecFileName}"
  

 gitUserName = sh('git config user.name').chomp
 info = "[#{gitUserName}] 提交信息"
 puts(info)
end

lane :push do 
spec_path = "Shining.podspec"
pod_push(path: spec_path, allow_warnings: true, use_libraries: false)

end
