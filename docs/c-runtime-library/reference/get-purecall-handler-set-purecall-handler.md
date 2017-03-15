---
title: "_get_purecall_handler, _set_purecall_handler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_purecall_handler"
  - "_set_purecall_handler_m"
  - "_get_purecall_handler"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_set_purecall_handler"
  - "_set_purecall_handler_m"
  - "set_purecall_handler_m"
  - "set_purecall_handler"
  - "stdlib/_set_purecall_handler"
  - "stdlib/_get_purecall_handler"
  - "_get_purecall_handler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_purecall_handler (función)"
  - "set_purecall_handler (función)"
  - "purecall_handler"
  - "set_purecall_handler_m (función)"
  - "_purecall_handler"
  - "_set_purecall_handler_m (función)"
  - "_get_purecall_handler (función)"
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _get_purecall_handler, _set_purecall_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene o establece el controlador de errores para una llamada de función virtual pura.  
  
## Sintaxis  
  
```  
typedef void (__cdecl* _purecall_handler)(void);  
  
_purecall_handler __cdecl _get_purecall_handler(void);  
  
_purecall_handler __cdecl _set_purecall_handler(   
   _purecall_handler function  
);  
```  
  
#### Parámetros  
 `function`  
 Función a la que se llamará cuando se llame a una función virtual pura. Una función `_purecall_handler` debe tener un tipo de valor devuelto void.  
  
## Valor devuelto  
 `_purecall_handler` anterior. Devuelve `nullptr` si no había controlador anterior.  
  
## Comentarios  
 El `_get_purecall_handler` y `_set_purecall_handler` funciones son específicas de Microsoft y se aplican sólo a código de C\+\+.  
  
 Una llamada a una función virtual pura es un error porque no tiene ninguna implementación. De forma predeterminada, el compilador genera código para invocar una función de controlador de error cuando se llama a una función virtual pura, que finaliza el programa. Puede instalar su propia función de controlador de errores para las llamadas de función virtual pura, contagiarse para depurar o con fines informativos. Para utilizar su propio controlador de errores, cree una función que tiene el `_purecall_handler` firma, a continuación, utilice `_set_purecall_handler` para que sea el controlador actual.  
  
 Dado que solo hay un `_purecall_handler` para cada proceso, al llamar a `_set_purecall_handler` inmediatamente afecta a todos los subprocesos. El último que llama en cualquiera de los subprocesos establece el controlador.  
  
 Para restaurar el comportamiento predeterminado, llame a `_set_purecall_handler` utilizando un `nullptr` argumento.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_get_purecall_handler`, `_set_purecall_handler`|\< cstdlib \> o \< stdlib.h \>|  
  
 Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// _set_purecall_handler.cpp  
// compile with: /W1  
#include <tchar.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
class CDerived;  
class CBase  
{  
public:  
   CBase(CDerived *derived): m_pDerived(derived) {};  
   ~CBase();  
   virtual void function(void) = 0;  
  
   CDerived * m_pDerived;  
};  
  
class CDerived : public CBase  
{  
public:  
   CDerived() : CBase(this) {};   // C4355  
   virtual void function(void) {};  
};  
  
CBase::~CBase()  
{  
   m_pDerived -> function();  
}  
  
void myPurecallHandler(void)  
{  
   printf("In _purecall_handler.");  
   exit(0);  
}  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
   _set_purecall_handler(myPurecallHandler);  
   CDerived myDerived;  
}  
```  
  
```Output  
In _purecall_handler.  
```  
  
## Vea también  
 [Control de errores](../../c-runtime-library/error-handling-crt.md)   
 [\_purecall](../../c-runtime-library/reference/purecall.md)