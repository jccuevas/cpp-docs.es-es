---
title: "threadprivate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "threadprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "threadprivate OpenMP directive"
ms.assetid: 3515aaed-6f9d-4d59-85eb-342378bea2d3
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# threadprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Especifica que una variable es privada para un subproceso.  
  
## Sintaxis  
  
```  
#pragma omp threadprivate(var)  
```  
  
## Comentarios  
 donde  
  
 `var`  
 Una lista separada por comas de variables que desea private a un subproceso.  `var` debe ser una variable global o de espacio de nombres\-scoped o una variable local static.  
  
## Comentarios  
 la directiva de `threadprivate` no admite ninguna cláusula de OpenMP.  
  
 Para obtener más información, vea [directiva de 2.7.1 threadprivate](../../../parallel/openmp/2-7-1-threadprivate-directive.md).  
  
 la directiva de `threadprivate` se basa en el atributo de [subproceso](../../../cpp/thread.md)`__declspec` ; los límites en **\_\_declspec \(subproceso\)** se aplican a `threadprivate`.  
  
 No puede utilizar `threadprivate` en ningún DLL que carga mediante [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175).  Esto incluye los archivos DLL cargados con [\/DELAYLOAD \(Retrasar importación de carga\)](../../../build/reference/delayload-delay-load-import.md), que también utiliza **LoadLibrary**.  
  
 Puede utilizar `threadprivate` en un archivo DLL que se carga dinámicamente en el inicio del proceso.  
  
 Dado que `threadprivate` se basa en **\_\_declspec \(subproceso\)**, una variable de `threadprivate` existirá en cualquier subproceso iniciado en el proceso, no sólo aquellos subprocesos que forman parte de un equipo de subproceso todos los generado por una región paralela.  Éste es un detalle de implementación de que quizás desee conocer, ya que puede observar, por ejemplo, los constructores de un tipo definido por el usuario de `threadprivate` denominado más a menudo a esperado.  
  
 Una variable de `threadprivate` de un tipo destructable no se garantiza que tener su destructor denominado.  Por ejemplo:  
  
```  
struct MyType   
{  
    ~MyType();  
};  
  
MyType threaded_var;  
#pragma omp threadprivate(threaded_var)  
int main()   
{  
    #pragma omp parallel  
    {}  
}  
```  
  
 Los usuarios no tienen ningún control respecto a cuando los subprocesos que constituyen la región paralela finalizarán.  Si existen esos subprocesos cuando los resultados de procesos, subprocesos no se notificadas sobre el resultado de procesos, y el destructor no se invoca para `threaded_var` en ningún subproceso excepto el salir \(aquí, el subproceso primario\).  El código no debe contar así en la destrucción adecuada de las variables de `threadprivate` .  
  
## Ejemplo  
 Para obtener un ejemplo de cómo utilizar `threadprivate`, vea [private](../../../parallel/openmp/reference/private-openmp.md).  
  
## Vea también  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)