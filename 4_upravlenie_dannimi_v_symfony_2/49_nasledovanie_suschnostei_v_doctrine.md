### 4.9 Наследование сущностей в Doctrine {#4-9-doctrine}

Типы наследований:

*   MappedSuperclass  
*   SingleTable
*   JoinedTable

**Class A** { prop 1; prop 2; }

**Class B extends A **{ prop 3; prop 4; }

**Class C extends A **{ prop 5; prop 6; }

*   MappedSuperclass

**Table B** (1 | 2 | 3 | 4 )

**Table C** (1 | 2 | 5 | 6 )

*   SingleTable

**Table A** (1 | 2 | 3 | 4 | 5 | 6 | Type [B/C] )

*   JoinedTable

**Table A** (id | 1 | 2 | Type [B/C] )

**Table B** (id | 3 | 4 )

**Table C** (id | 5 | 6 )