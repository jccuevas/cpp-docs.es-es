---
---
# <a name="compiler-warning-level-1-c4055"></a>Advertencia del compilador (nivel 1) C4055  
  
'conversion': del puntero de datos 'type1' al puntero de función 'type2'  
  
**Obsoleto:** 2017 de Visual Studio y versiones posteriores no genera esta advertencia.

 Un puntero de datos se convierte (quizás incorrectamente) en un puntero de función. Se trata de una advertencia de nivel 1 en /Za y una advertencia de nivel 4 en /Ze.  
  
 El ejemplo siguiente genera la advertencia C4055:  
  
```C  
// C4055.c  
// compile with: /Za /W1 /c  
typedef int (*PFUNC)();  
int *pi;  
PFUNC f() {  
   return (PFUNC)pi;   // C4055  
}  
```  
  
 En /Ze, esta es una advertencia de nivel 4.  
  
```C  
// C4055b.c  
// compile with: /W4 /c  
typedef int (*PFUNC)();  
int *pi;  
PFUNC f() {  
return (PFUNC)pi;   // C4055  
}  
```