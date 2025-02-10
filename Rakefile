require "bundler/gem_tasks"
require "stackprof"
require "rack/test"

task :make_dump do
  class DummyA
    def work
      sleep 0.01
    end
  end

  class DummyB
    def work
      DummyA.new.work
    end
  end

  StackProf.run(mode: :cpu, out: 'spec/fixtures/test.dump') do
    Array.new(1000).each { DummyB.new.work }

  end

  StackProf.run(mode: :cpu, raw: true, out: 'spec/fixtures/test-raw.dump') do
    Array.new(1000).each { DummyB.new.work }
  end
end
