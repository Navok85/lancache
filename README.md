LANCACHE in Docker (fork from https://github.com/bntjah/lancache)
 - nginx
 - unbound (DNS)
 - sniproxy

Monitoring:
* watch -n 30 du -sch /pool1/lancache/
* iftop -i enp3s0f0
* nload -U G - u M -i 102400 -o 102400

Check file limit with: 	ulimit -n

tmux: 
 - strg+b / " für horizontal splitten
 - strg+b / % für vertikal splitten
