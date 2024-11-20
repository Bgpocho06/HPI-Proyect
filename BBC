# MIT License
# 
# Copyright (c) 2024 BBC
# 
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.

tasks = {
    "HPI Project": ["2024-11-21, 16:00", 6],
    "MD Exam": ["2025-01-11, 11:00", 10],
    "AG Questionnaires": ["2024-06-07, 16:00", 3]
}

from datetime import datetime

def date_difference(date):
    now = datetime.now()
    date_obj = datetime.strptime(date, "%Y-%m-%d, %H:%M")
    date_difference = (date_obj - now).total_seconds() / (3600 * 24)
    return date_difference

def prioritize(tasks, date_imp=0.75):
    dfct_imp = 1 - date_imp
    print("You should consider this order of priority:\n" + "-" * 43)
    importances = []
    for task, conditions in tasks.items():
        deadline, dfct = conditions
        time_period = date_difference(deadline)
        ponderation = date_imp * (1 / (1 + time_period)) + dfct_imp / 10 * dfct
        importances.append((ponderation, task))
    importances.sort(reverse=True)
    for n, tasks in enumerate(importances, start=1):
        print(f"{n}.- {tasks[1]}")

prioritize(tasks)
