---
title: Sobrecargas de plantillas seguras | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
dev_langs:
- C++
helpviewer_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
- secure template overloads
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f1a4731ef2e11f87538bc87d8aa8670c174f0dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412470"
---
# <a name="secure-template-overloads"></a>Sobrecargas de plantilla seguras
Microsoft ha dejado de usar muchas funciones de la biblioteca en tiempo de ejecución (CRT) en favor de versiones con seguridad mejorada. Por ejemplo, `strcpy_s` es la sustitución más segura para `strcpy`. Las funciones en desuso son orígenes comunes de errores de seguridad, ya que no impiden operaciones que pueden sobrescribir la memoria. De forma predeterminada, el compilador genera una advertencia de desuso cuando se usa una de estas funciones. La biblioteca CRT proporciona sobrecargas de plantilla de C++ para estas funciones con el fin de facilitar la transición a variantes más seguras.  
  
Por ejemplo, este fragmento de código genera una advertencia porque `strcpy` está en desuso:  
  
```cpp  
char szBuf[10];  
strcpy(szBuf, "test"); // warning: deprecated  
```
  
La advertencia de desuso está ahí para indicarle que su código puede no ser seguro. Si ha comprobado que el código no puede sobrescribir la memoria, dispone de varias opciones. Para suprimir la advertencia, puede omitir la advertencia, puede definir el símbolo `_CRT_SECURE_NO_WARNINGS` antes de incluir las instrucciones "include" para los encabezados de CRT o puede actualizar el código para usar `strcpy_s`:  
  
```cpp  
char szBuf[10];  
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function  
```
  
Las sobrecargas de plantilla proporcionan opciones adicionales. Si define `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` como 1, se permiten sobrecargas de plantillas de funciones CRT estándar que llaman automáticamente a variantes más seguras. Si `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` es 1, no es necesario ningún cambio en el código. En segundo plano, la llamada a `strcpy` se cambia a una llamada a `strcpy_s` con el argumento de tamaño suministrado automáticamente.  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1  
  
// ...  
  
char szBuf[10];  
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")  
```  
  
La macro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` no afecta a las funciones que toman un recuento, como `strncpy`. Para habilitar las sobrecargas de plantilla para las funciones de recuento, defina `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` como 1. Antes de hacerlo, sin embargo, asegúrese de que el código pasa el número de caracteres, no el tamaño del búfer (un error común). Además, el código que escribe explícitamente un terminador nulo al final del búfer después de la llamada a la función no es necesario si se llama a la variante segura. Si necesita comportamiento de truncamiento, consulte [_TRUNCATE](../c-runtime-library/truncate.md).  
  
> [!NOTE]
>  La macro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` requiere que `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` también se defina como 1. Si `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` se define como 1 y `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` se define como 0, la aplicación no realizará ninguna sobrecarga de plantilla.  
  
Cuando se define `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` como 1, se permiten sobrecargas de plantilla de las variantes seguras (nombres que terminan en "_s"). En este caso, si `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` es 1, se debe realizar entonces un pequeño cambio en el código original:  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1  
  
// ...  
  
char szBuf[10];  
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")  
```  
  
 Solo es necesario cambiar el nombre de la función (agregando "_s"); la sobrecarga de plantilla se ocupa de proporciona el argumento de tamaño.  
  
 De forma predeterminada, `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` y `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` se definen como 0 (deshabilitado) y `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` se define como 1 (habilitado).  
  
 Tenga en cuenta que estas sobrecargas de plantilla solo funcionan con matrices estáticas. Los búferes asignados de forma dinámica requieren cambios adicionales en el código fuente. Examinando de nuevo los ejemplos anteriores:  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1  
  
// ...  
  
char *szBuf = (char*)malloc(10);  
strcpy(szBuf, "test"); // still deprecated; you have to change it to  
                       // strcpy_s(szBuf, 10, "test");  
```  
  
 Y esto:  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1  
  
// ...  
  
char *szBuf = (char*)malloc(10);  
strcpy_s(szBuf, "test"); // doesn't compile; you have to change it to  
                         // strcpy_s(szBuf, 10, "test");  
```  
  
## <a name="see-also"></a>Vea también  
 [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md)   
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)