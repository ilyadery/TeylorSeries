# TeylorSeries
1.Написать программу для расчета по двум формулам.
Z1=cos a+sin a+cos 3a+sin 3a
Z2=2sin a

Код:
 double a, b, c, d;
            if (textBox1.Text == "")
            {
                textBox2.Text = "Не все данные введены";
            }
            else
            {
                a = double.Parse(textBox1.Text);
                b = Math.Cos(a) + Math.Sin(a) + Math.Cos(3 * a) + Math.Sin(a);
                textBox2.Text = b.ToString();
            }

            if (textBox3.Text == "")
            {
                textBox4.Text = "Не все данные введены";
            }
            else
            {
                c = double.Parse(textBox3.Text);
                d = 2*Math.Sin(c);
                textBox4.Text = d.ToString();
            }
  
2.Написать программу, которая по введеному значению аргумента вычисляет значение функции, заданной в виде графика. Параметр R вводится с клавиатуры

Код:

            double num = double.Parse(this.textBox5.Text);
            bool flag = num <= 0.0;
            double value;
            if (flag)
            {
                value = 0.5 * num;
            }
            else
            {
                bool flag2 = num <= 2.0;
                if (flag2)
                {
                    value = 2.0 - Math.Sqrt(4.0 - num * num);
                }
                else
                {
                    bool flag3 = num < 4.0;
                    if (flag3)
                    {
                        value = Math.Sqrt(4.0 - (num - 2.0) * (num - 2.0));
                    }
                    else
                    {
                        value = 4.0 - num;
                    }
                }
            }
            this.textBox6.Text = string.Concat(new object[]
            {
                "f(",
                num,
                ") = ",
                Math.Round(value, 3)
            });

3.Вычислить и вывести на экран в виде таблицы значения функции, заданой с помощью ряда Тейлора.

Код:
double num = double.Parse(this.textBox7.Text);
            double num2 = double.Parse(this.textBox8.Text);
            double num3 = double.Parse(this.textBox9.Text);
            double num4 = double.Parse(this.textBox10.Text);
            this.listBox1.Items.Clear();
            this.listBox1.Items.Add("|   x\t|   f(x)\t|   steps\t|");
            for (double num5 = num; num5 < num2; num5 += num3)
            {
                double num6 = num5;
                double num7 = num5;
                int num8 = 1;
                while (Math.Abs(num7) > num4)
                {
                    num8++;
                    num7 = -num7 * num5 * num5;
                    num6 += num7 / (double)(2 * num8 - 1);
                }
                this.listBox1.Items.Add(string.Concat(new object[]
                {
                    "| ",
                    num5.ToString("n"),
                    "\t| ",
                    num6.ToString("n"),
                    "\t| ",
                    num8,
                    "\t|"
                }));
