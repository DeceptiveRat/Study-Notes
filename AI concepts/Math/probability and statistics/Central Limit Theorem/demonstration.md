# Central Limit Theorem Demonstration Script

Python script demonstrating the Central Limit Theorem using uniform and exponential population distributions with Matplotlib.

> [!example]- Simulation Script: *demonstration.py* (Click to expand)
> ```python
> #!/bin/python3 
>
> import numpy as np
> import matplotlib.pyplot as plt
> import sys
> import getopt
>
> def progress_bar(iteration, total, length=150):
>         # since indices start with 0
>         iteration += 1
>         percent = f"{100*(iteration/float(total)):.1f}"
>         filled_length = int(length * iteration // total)
>         bar = "[" + "="*filled_length + " " * (length - filled_length) + "]"
>         sys.stdout.write(f'\r{bar}\t{percent}% ({iteration}/{total}) complete')
>         if iteration == total:
>                 print()
>         sys.stdout.flush()
>
> def usage():
>         print("usage:", sys.argv[0])
>         print("options:")
>         print("-h: display this help screen")
>         print("-s <int>: sample size. Defaults to 10")
>         print("-c <int>: sample count. Defaults to 10")
>         print("-r: only use replacing choices. Makes it much quicker")
>
> try:
>         opts, args = getopt.getopt(sys.argv[1:], "hs:c:r")
> except getopt.GetoptError as err:
>         print(err)
>         usage()
>         sys.exit(2)
>
> sample_size=10 
> sample_count=10
> only_replace = False
>
> for option, argument in opts:
>         if option == "-h":
>                 usage()
>                 sys.exit()
>         elif option == "-s":
>                 sample_size = int(argument)
>         elif option == "-c":
>                 sample_count = int(argument)
>         elif option == "-r":
>                 only_replace = True
>         else:
>                 assert False, "unhandled option"
>
> # create population
> np.random.seed(42)
> population = np.random.randint(low=0, high=10000, size=1000000)
> population_exp = np.random.exponential(scale=2, size=1000000)
>
> # visualize population
> fig = plt.figure()
> if only_replace:
>         ax1 = fig.add_subplot(221)
>         ax2 = fig.add_subplot(222)
> else:
>         ax1 = fig.add_subplot(321)
>         ax2 = fig.add_subplot(322)
> ax1.hist(population)
> ax2.hist(population_exp)
> ax1.title.set_text("population distribution")
> ax2.title.set_text("population distribution (exponential)")
>
> # choose samples
> if  not only_replace:
>         sample_means = []
>         print("getting sample...")
>         for _ in range(sample_count):
>                 sample = np.random.choice(population, size=sample_size, replace=False)
>                 sample_means.append(np.mean(sample))
>                 progress_bar(_, sample_count)
>         ax3 = fig.add_subplot(323)
>         ax3.hist(sample_means)
>         ax3.title.set_text("sample")
>
>         sample_means = []
>         print("getting sample (exponential)...")
>         for _ in range(sample_count):
>                 sample = np.random.choice(population_exp, size=sample_size, replace=False)
>                 sample_means.append(np.mean(sample))
>                 progress_bar(_, sample_count)
>         ax4 = fig.add_subplot(324)
>         ax4.hist(sample_means)
>         ax4.title.set_text("sample (exponential)")
>
> sample_means = []
> print("getting sample (replace)...")
> for _ in range(sample_count):
>         sample = np.random.choice(population, size=sample_size, replace=True)
>         sample_means.append(np.mean(sample))
>         progress_bar(_, sample_count)
> if only_replace:
>         ax5 = fig.add_subplot(223)
> else:
>         ax5 = fig.add_subplot(325)
> ax5.hist(sample_means)
> ax5.title.set_text("sample (replace)")
>
> sample_means = []
> print("getting sample (replace) (exponential)...")
> for _ in range(sample_count):
>         sample = np.random.choice(population_exp, size=sample_size, replace=True)
>         sample_means.append(np.mean(sample))
>         progress_bar(_, sample_count)
> if only_replace:
>         ax6 = fig.add_subplot(224)
> else:
>         ax6 = fig.add_subplot(326)
> ax6.hist(sample_means)
> ax6.title.set_text("sample (replace) (exponential)")
>
> plt.show()
> ```
