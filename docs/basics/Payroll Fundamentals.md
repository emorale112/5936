# Payroll Fundamentals

Payroll in its entirety is rather complex, but the API is designed to shield as much complexity as possible from the end user, without sacrificing functionality. This section gives a birds-eye view of the objects that make up the [Gusto system](gusto.com).

Starting with an authenticated user, you will notice that they may be administrators for multiple companies. This is not uncommon, and your application should prepare for it. Accountants use Gusto to manage payroll for many companies simultaneously.


Companies themselves are, naturally, a collection of one to hundreds of employees. Employee data, on the payroll side, is relatively static. Compensation information, addresses, and tax information changes rather infrequently once set.

Companies can have multiple work locations, across multiple states, but everyone gets paid at the same time.

Pay periods are the combination of a company, a subset of its employees, and a time range. Not every employee at a company will be a part of every payroll. One-off (or'off-cycle') payrolls are run for special events such as hiring or termination, and employees can be excluded from payrolls.

Regular payrolls are tied to a specific pay periods, and all associated information - vacation & sick time, hours worked, bonuses, etc. - should be applied to that time range.

