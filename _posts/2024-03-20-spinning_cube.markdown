---
title:  "[JS] 회전하는 사각형"
date:   2024-03-20 21:44:00 +0900
categories: JS
---

## 🎠 프로젝트 소개

- 자바스크립트를 이용한 x, y, z축으로 회전하는 3D 큐브(사각형)


## 프로젝트 계기

- 유튜브에서 [도넛을 회전시키는 영상](https://www.youtube.com/watch?v=rj7DOPPTkQA&ab_channel=ServetGulnaroglu)을 보고 비슷한 프로그램을 만들고 싶어서 시작함.


## 📡 실행 주소

[http://wkd3ogks.github.io/spinning-cube](http://wkd3ogks.github.io/spinning-cube).


## 🛠 핵심 코드
{% highlight javascript %} 
class Square {
    constructor(x, y, size) {
        this.h = -150;
        this.d = -200;
        this._size = size;
        this._context = canvas.getContext('2d');
        this._origin = [x / 2, y / 2];
        this._context.translate(...this._origin);
        this.vertex_size = 8;
        this.vertex_3d = new Array(this.vertex_size);
        this.vertex_2d = new Array(this.vertex_size);
    }
    display() {
        this.vertex_3d = [
            [this._size, this._size, this._size],
            [-this._size, this._size, this._size],
            [-this._size, -this._size, this._size],
            [this._size, -this._size, this._size], 
            [this._size, this._size, -this._size],
            [-this._size, this._size, -this._size],
            [-this._size, -this._size, -this._size],
            [this._size, -this._size, -this._size], 
        ];
        this._context.clearRect(...this._origin.map((num) => -num), canvas.width, canvas.height);
        for(let i = 0; i < this.vertex_2d.length; i++) {
            this.vertex_2d[i] = [this.d / (this.h + this.vertex_3d[i][2]) * this.vertex_3d[i][0], this.d / (this.h + this.vertex_3d[i][2]) * this.vertex_3d[i][1]];
        }
        this._draw_box();
    }
    _draw_box() {
        for(let i = 0; i < 4; i++) {
            this._draw_line(i, (i + 1) % 4);
            this._draw_line(i + 4, ((i + 1) % 4) + 4);
            this._draw_line(i, i + 4);
        } 
    }
    _draw_line(idx_1, idx_2) {
        const line = canvas.getContext("2d");
        line.beginPath();
        line.moveTo(...this.vertex_2d[idx_1]);
        line.lineTo(...this.vertex_2d[idx_2]);
        line.stroke();
    }

    rotateZ(theta) {
        this._context.clearRect(...this._origin.map((num) => -num), canvas.width, canvas.height);
        for(let i = 0; i < this.vertex_size; i++) {
            this.vertex_3d[i] = [
                this.vertex_3d[i][0] * Math.cos(theta) - this.vertex_3d[i][2] * Math.sin(theta), 
                this.vertex_3d[i][1], 
                this.vertex_3d[i][2] * Math.cos(theta) + this.vertex_3d[i][0] * Math.sin(theta)
            ];
            this.vertex_2d[i] = [this.d / (this.h + this.vertex_3d[i][2]) * this.vertex_3d[i][0], this.d / (this.h + this.vertex_3d[i][2]) * this.vertex_3d[i][1]];
        }
        this._draw_box();
    }

    rotateY(theta) {
        this._context.clearRect(...this._origin.map((num) => -num), canvas.width, canvas.height);

        for(let i = 0; i < this.vertex_size; i++) {
            this.vertex_3d[i] = [
                this.vertex_3d[i][0], 
                this.vertex_3d[i][1] * Math.cos(theta) - this.vertex_3d[i][2] * Math.sin(theta), 
                this.vertex_3d[i][2] * Math.cos(theta) + this.vertex_3d[i][1] * Math.sin(theta)
            ];

            this.vertex_2d[i] = [this.d / (this.h + this.vertex_3d[i][2]) * this.vertex_3d[i][0], this.d / (this.h + this.vertex_3d[i][2]) * this.vertex_3d[i][1]];
        }
        this._draw_box();
    }
    rotateX(theta) {
        this._context.clearRect(...this._origin.map((num) => -num), canvas.width, canvas.height);

        for(let i = 0; i < this.vertex_size; i++) {
            this.vertex_3d[i] = [
                this.vertex_3d[i][0] * Math.cos(theta) + this.vertex_3d[i][1] * Math.sin(theta),
                this.vertex_3d[i][1] * Math.cos(theta) - this.vertex_3d[i][0] * Math.sin(theta),
                this.vertex_3d[i][2]
            ];
            
            this.vertex_2d[i] = [this.d / (this.h + this.vertex_3d[i][2]) * this.vertex_3d[i][0], this.d / (this.h + this.vertex_3d[i][2]) * this.vertex_3d[i][1]];
        }
        this._draw_box();
    }
    run() {
        square.display();
        setInterval(() => {
            square.rotateX(slider[0].value / 100);
            speed_display[0].innerHTML = slider[0].value / 100;
        }, 100)
        setInterval(() => {
            square.rotateY(slider[1].value / 100);
            speed_display[1].innerHTML = slider[1].value / 100;
        }, 100)
        setInterval(() => {
            square.rotateZ(slider[2].value / 100);
            speed_display[2].innerHTML = slider[2].value / 100;
        }, 100)
    }
    reset() {
        for(let i = 0; i < 3; i++) {
            slider[i].value = 0;
        }
        square.display();
    }
}
{% endhighlight %}

