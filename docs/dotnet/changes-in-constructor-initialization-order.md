---
title: "Cambios en el orden de inicializaci&#243;n de constructores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "constructores, C++"
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Cambios en el orden de inicializaci&#243;n de constructores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El orden de inicialización de los constructores de clase ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
## Comparación del orden de inicialización de constructores  
 En Extensiones administradas para C\+\+, la inicialización de constructores tenía lugar en siguiente orden:  
  
1.  Se invoca al constructor de la clase base, si hay alguno.  
  
2.  Se evalúa la lista de inicializaciones de la clase.  
  
3.  Se ejecuta el cuerpo del código del constructor de clase.  
  
 Este orden de ejecución se ajusta a las mismas convenciones que en la programación de C\+\+ nativa.  El nuevo lenguaje Visual C\+\+ recomienda el siguiente orden de ejecución para las clases CLR:  
  
1.  Se evalúa la lista de inicializaciones de la clase.  
  
2.  Se invoca al constructor de la clase base, si hay alguno.  
  
3.  Se ejecuta el cuerpo del código del constructor de clase.  
  
 Observe que este cambio sólo se aplica a las clases CLR; las clases nativas de [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)] siguen ajustándose a las convenciones anteriores.  En ambos casos, estas reglas se aplican en cascada ascendente en toda la cadena de jerarquía de una clase determinada.  
  
 Observe el siguiente ejemplo de código, donde se utilizan las Extensiones administradas para C\+\+:  
  
```  
__gc class A  
{  
public:  
   A() : _n(1)  
   {  
   }  
  
protected:  
   int _n;  
};  
  
__gc class B : public A  
{  
public:  
   B() : _m(_n)  
   {  
   }  
private:  
   int _m;  
};  
```  
  
 Siguiendo el orden de inicialización de constructores recomendado anteriormente, debería observarse el siguiente orden de ejecución cuando se construyen nuevas instancias de la clase `B`:  
  
1.  Se invoca el constructor de la clase base `A`.  El miembro `_n` se inicializa en `1`.  
  
2.  Se evalúa la lista de inicializaciones para la clase `B`.  El miembro `_m` se inicializa en `1`.  
  
3.  Se ejecuta el cuerpo del código de la clase `B`.  
  
 Ahora, observe este mismo código en la nueva sintaxis de Visual C\+\+:  
  
```  
ref class A  
{  
public:  
   A() : _n(1)  
   {  
   }  
  
protected:  
   int _n;  
};  
  
ref class B : A  
{  
public:  
   B() : _m(_n)  
   {  
   }  
private:  
   int _m;  
};  
```  
  
 En la nueva sintaxis, el orden de ejecución cuando se construyen las nuevas instancias de la clase `B` es el siguiente:  
  
1.  Se evalúa la lista de inicializaciones para la clase `B`.  El miembro `_m` se inicializa en `0` \(`0` es el valor sin inicializar del miembro de clase `_m`\).  
  
2.  Se invoca el constructor de la clase base `A`.  El miembro `_n` se inicializa en `1`.  
  
3.  Se ejecuta el cuerpo del código de la clase `B`.  
  
 Observe que una sintaxis similar genera resultados diferentes para estos ejemplos de código.  El constructor de la clase `B` depende de un valor de la clase base `A` para inicializar su miembro.  Sin embargo, todavía no se ha invocado el constructor para la clase `A`.  Este tipo de dependencia puede resultar especialmente peligrosa si la clase heredada depende de que tenga lugar una asignación de memoria o de recursos en el constructor de la clase base.  
  
## Qué significa pasar de Extensiones administradas para C\+\+ a Visual C\+\+ 2010  
 En muchos casos, los cambios en el orden de ejecución de los constructores de clase deberían ser transparentes para el programador ya que las clases base no tienen ninguna noción del comportamiento de las clases heredadas.  Sin embargo, tal y como se muestra en estos ejemplos de código, los constructores de clases heredadas pueden verse muy afectados cuando sus listas de inicialización dependen de los valores de los miembros de la clase base.  Cuando pase el código de Extensiones administradas para C\+\+ a la nueva sintaxis, considere la posibilidad de trasladar estas construcciones al cuerpo del constructor de la clase, para garantizar que la ejecución se produzca finalmente.  
  
## Vea también  
 [Tipos administrados \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [Constructores](../cpp/constructors-cpp.md)   
 [Inicializadores de constructor](../misc/constructor-initializers.md)