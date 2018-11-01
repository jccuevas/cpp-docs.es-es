---
title: Reglas de modo por lotes
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 46387fc13c28d95d7b19fb18774daa6fc3064970
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429775"
---
# <a name="batch-mode-rules"></a>Reglas de modo por lotes

```
{frompath}.fromext{topath}.toext::
   commands
```

Las reglas de inferencia de modo por lotes proporcionan sólo una llamada de la regla de inferencia cuando los comandos N pasan por esta regla de inferencia. Sin reglas de inferencia de modo por lotes, es necesario que los comandos de N que se debe invocar. N es el número de elementos dependientes que desencadenan la regla de inferencia.

Archivos MAKE que contienen las reglas de inferencia de modo por lotes deben usar NMAKE versión 1.62 o superior. Para comprobar la versión NMAKE, ejecute la macro _NMAKE_VER que está disponible con la versión de NMAKE 1.62 o superior. Esta macro devuelve una cadena que representa la versión de producto de Visual C++.

La única diferencia sintáctica de la regla de inferencia estándar es que la regla de inferencia de modo por lotes se termina con dos puntos dobles (::).

> [!NOTE]
>  La herramienta que se va a invocar debe ser capaz de controlar varios archivos. Debe usar la regla de inferencia de modo por lotes `$<` como la macro para tener acceso a los archivos dependientes.

Las reglas de inferencia de modo por lotes pueden acelerar el proceso de compilación. Resulta más rápido que proporcione archivos al compilador en proceso por lotes, ya que el controlador del compilador se invoca una sola vez. Por ejemplo, el compilador de C y C++ funciona mejor cuando el control de un conjunto de archivos porque puede permanecer en memoria durante el proceso.

El ejemplo siguiente muestra cómo usar las reglas de inferencia de modo por lotes:

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

NMAKE genera el siguiente resultado sin reglas de inferencia de modo por lotes:

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

## <a name="see-also"></a>Vea también

[Reglas de inferencia](../build/inference-rules.md)