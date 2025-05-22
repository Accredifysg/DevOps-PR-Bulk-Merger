require_relative "bulk_merger"

abort('abort: GITHUB_TOKEN not set in environment.') unless ENV['GITHUB_TOKEN']

desc "Warn user about releasing gems and k8s deployments"
task :warning do

  puts <<~WARNING
  ⚠️ WARNING ⚠️

  You are about to run a script that will bulk-merge pull requests.
  Proceed with caution. If you are unsure about any part of this process, consult with your team.
  
  WARNING
end

desc "Just approve pull requests"
task :review do
  BulkMerger.approve_unreviewed_pull_requests!
end

desc "Approve & merge pull requests"
task :merge => :warning do
  BulkMerger.approve_unreviewed_pull_requests!
  BulkMerger.merge_approved_pull_requests!
end

desc "Merge approved pull requests, without reviewing"
task :merge_only => :warning do
  BulkMerger.merge_approved_pull_requests!
end

desc "List un-reviewed pull requests"
task :list do
  BulkMerger.approve_unreviewed_pull_requests!(list: true)
end
