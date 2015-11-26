Vagrant.configure(2) do |config|
  config.vm.define "boot2docker"
  config.vm.box = "yungsang/boot2docker"
  config.vm.synced_folder "./data", "/vagrant"
  config.vm.network :forwarded_port, guest: 3306, host: 3306
  config.vm.network :forwarded_port, guest: 6379, host: 6379
  config.vm.network :forwarded_port, guest: 9200, host: 9200

  config.vm.provision :shell do |s|
    s.inline = <<-EOT
    echo 'Start Elasticsearch docker build -t elasticsearch-plugins .'
    docker run -d -p 9200:9200 -v /vagrant/elasticsearch/data:/usr/share/elasticsearch/data elasticsearch-plugins
	echo 'Start MySQl'
    docker run -p "3306:3306" -v /vagrant/mysql:/var/lib/mysql -e MYSQL_ADMIN_PASS="123" -d dgraziotin/mysql
	echo 'Start Redis'
    docker run -p "6379:6379" -d redis
    EOT
  end
end