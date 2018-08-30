---
title: threadprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- threadprivate
dev_langs:
- C++
helpviewer_keywords:
- threadprivate OpenMP directive
ms.assetid: 3515aaed-6f9d-4d59-85eb-342378bea2d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0502528a2db47b8db41437fd7017aece1dc67cde
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217750"
---
# <a name="threadprivate"></a>threadprivate
Especifica que una variable privada a un subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma omp threadprivate(var)  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `var`  
 Una lista separada por comas de variables que desea convertir en privado a un subproceso. `var` debe ser una variable global o espacio de nombres de ámbito o una variable local estática.  
  
## <a name="remarks"></a>Comentarios  
 El `threadprivate` directiva es compatible con ningún cláusulas de OpenMP.  
  
 Para obtener más información, consulte [2.7.1 threadprivate (directiva)](../../../parallel/openmp/2-7-1-threadprivate-directive.md).  
  
 El `threadprivate` directiva se basa en el [subproceso](../../../cpp/thread.md) `__declspec` atributo; límites en **__declspec (Thread)** se aplican a `threadprivate`.  
  
 No puede usar `threadprivate` en cualquier archivo DLL que se cargan a través de [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175).  Esto incluye los archivos DLL que se cargan con [/DELAYLOAD (Retrasar importación de carga)](../../../build/reference/delayload-delay-load-import.md), que también utiliza **LoadLibrary**.  
  
 Puede usar `threadprivate` en un archivo DLL que se carga estáticamente al iniciarse el proceso.  
  
 Dado que `threadprivate` se basa en **__declspec (Thread)**, un `threadprivate` variable existirá en cualquier subproceso que inició en el proceso, no solo entre los subprocesos que forman parte de un grupo de subprocesos generado por una región paralela.  Se trata de un detalle de implementación que desea tener en cuenta, ya que se pueden observar, por ejemplo, los constructores de una `threadprivate` llamado más a menudo, a continuación, se esperaba el tipo definido por el usuario.  
  
 Un `threadprivate` variable de un tipo destructable no se garantiza que tiene su destructor denominado.  Por ejemplo:  
  
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
  
 Los usuarios no tienen ningún control sobre cuándo se terminarán los subprocesos que constituyen la región paralela.  Si esos subprocesos existen cuando se cierra el proceso, los subprocesos no notificará acerca de la salida del proceso y el destructor no se llamará para `threaded_var` en cualquier subproceso, excepto en el que se cierra (aquí, el subproceso principal).  Por lo que el código no debe tener en cuenta en la destrucción correcta de `threadprivate` variables.  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo del uso de `threadprivate`, consulte [privada](../../../parallel/openmp/reference/private-openmp.md).  
  
## <a name="see-also"></a>Vea también  
 [Directivas](../../../parallel/openmp/reference/openmp-directives.md)