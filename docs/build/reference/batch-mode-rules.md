---
title: Reglas de modo por lotes
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 38402e7b8a937cebb823ce13fa1ac01fc1099878
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328410"
---
# <a name="batch-mode-rules"></a>Reglas de modo por lotes

```
{frompath}.fromext{topath}.toext::
   commands
```

Las reglas de inferencia de modo por lotes proporcionan solo una invocación de la regla de inferencia cuando los comandos N pasan por esta regla de inferencia. Sin reglas de inferencia de modo por lotes, requeriría que se invocaran comandos N. N es el número de dependientes que desencadenan la regla de inferencia.

Los archivos Make que contienen reglas de inferencia de modo por lotes deben usar NMAKE versión 1.62 o superior. Para comprobar la versión NMAKE, ejecute la macro de _NMAKE_VER disponible con NMAKE versión 1.62 o superior. Esta macro devuelve una cadena que representa la versión del producto Visual C++.

La única diferencia sintáctica de la regla de inferencia estándar es que la regla de inferencia de modo por lotes se termina con dos puntos (::).

> [!NOTE]
> La herramienta que se invoca debe ser capaz de controlar varios archivos. La regla de inferencia `$<` de modo por lotes debe utilizarse como macro para tener acceso a archivos dependientes.

Las reglas de inferencia de modo por lotes pueden acelerar el proceso de compilación. Es más rápido proporcionar archivos al compilador por lotes, porque el controlador del compilador se invoca solo una vez. Por ejemplo, el compilador C y C++ funciona mejor al controlar un conjunto de archivos porque puede permanecer residente de memoria durante el proceso.

En el ejemplo siguiente se muestra cómo utilizar reglas de inferencia de modo por lotes:

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

NMAKE produce la salida siguiente sin reglas de inferencia de modo por lotes:

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

NMAKE produce el siguiente resultado con las reglas de inferencia de modo por lotes:

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

## <a name="see-also"></a>Consulte también

[Reglas de inferencia](inference-rules.md)
