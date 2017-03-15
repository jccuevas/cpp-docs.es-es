---
title: "Reglas de modo por lotes | Microsoft Docs"
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
  - "reglas de inferencia de procesamiento por lotes en NMAKE"
  - "reglas de inferencia en NMAKE"
  - "NMAKE (programa), reglas de inferencia"
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Reglas de modo por lotes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

```  
{frompath}.fromext{topath}.toext::  
   commands  
```  
  
 Las reglas de inferencia de modo por lotes proporcionan sólo una llamada de la regla de inferencia cuando los comandos N pasan por esta regla de inferencia.  Sin las reglas de inferencia de modo por lotes, habría que llamar a comandos N.  N es el número de dependientes que desencadenan la regla de inferencia.  
  
 Los archivos MAKE que contienen las reglas de inferencia de modo por lotes deben usar la versión 1.62 o superior de NMAKE.  Para comprobar la versión de NMAKE, se ha de ejecutar la macro \_NMAKE\_VER que está disponible con la versión 1.62 o superior de NMAKE.  Esta macro devuelve una cadena que representa la versión de producto de Visual C\+\+.  
  
 La única diferencia sintáctica de la regla de inferencia estándar es que la regla de inferencia de modo por lotes termina con un signo doble de dos puntos \(::\).  
  
> [!NOTE]
>  La herramienta a la que se llama debe poder controlar varios archivos.  La regla de inferencia de modo por lotes debe usar `$<` como macro para tener acceso a archivos dependientes.  
  
 Las reglas de inferencia de modo por lotes pueden acelerar el proceso de compilación.  Es más rápido proporcionar archivos al compilador en lotes, dado que sólo se llama una vez al controlador del compilador.  Por ejemplo, el compilador de C y C\+\+ funciona mejor cuando se controla un conjunto de archivos porque puede permanecer en memoria durante el proceso.  
  
 El siguiente ejemplo muestra cómo se utilizan las reglas de inferencia de modo por lotes:  
  
```  
#  
# sample makefile to illustrate batch-mode inference rules  
#  
O = .  
S = .  
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj  
CFLAGS = -nologo  
  
all : $(Objs)  
  
!ifdef NOBatch  
{$S}.cpp{$O}.obj:  
!else  
{$S}.cpp{$O}.obj::  
!endif  
   $(CC) $(CFLAGS) -Fd$O\ -c $<  
  
$(Objs) :  
  
#end of makefile  
```  
  
 NMAKE genera el siguiente resultado sin las reglas de inferencia de modo por lotes:  
  
```  
E:\tmp> nmake -f test.mak -a NOBatch=1  
  
Microsoft (R) Program Maintenance Utility   Version 7.00.0000  
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.  
        cl -nologo -Fd.\ -c .\foo1.cpp  
foo1.cpp  
        cl -nologo -Fd.\ -c .\foo2.cpp  
foo2.cpp  
        cl -nologo -Fd.\ -c .\foo3.cpp  
foo3.cpp  
        cl -nologo -Fd.\ -c .\foo4.cpp  
foo4.cpp  
```  
  
 NMAKE genera el siguiente resultado con las reglas de inferencia de modo por lotes:  
  
```  
E:\tmp> nmake -f test.mak -a  
  
Microsoft (R) Program Maintenance Utility   Version 7.00.0000  
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.  
  
        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp  
foo1.cpp  
foo2.cpp  
foo3.cpp  
foo4.cpp  
Generating Code...  
```  
  
## Vea también  
 [Reglas de inferencia](../build/inference-rules.md)