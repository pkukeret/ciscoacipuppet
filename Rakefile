require 'puppetlabs_spec_helper/rake_tasks'

desc 'Task to build puppet module and install it'
task :build do
  puppet_version = Facter.value(:puppetversion)
  fail "Can't find a puppet version." if puppet_version.nil?
  build_cmd = 'puppet module build'
  uninstall_cmd = 'puppet module uninstall cisco-cisco_aci --force'
  install_cmd = 'puppet module install pkg/cisco-cisco_aci*gz'
  sh "#{build_cmd}"
  sh "#{uninstall_cmd}" do |ok, res|
  end
  sh "#{install_cmd}"
end

desc 'run rspec'
task :spec do
  rspec_cmd = 'rspec'
  RSPEC_OPTS = [
    '--color',
    '--format documentation',
  ].join(' ')
  sh "#{rspec_cmd} #{RSPEC_OPTS} spec/acceptance/**/*.rb"
end
