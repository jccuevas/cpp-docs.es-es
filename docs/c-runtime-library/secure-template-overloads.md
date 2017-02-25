---
title: "Sobrecargas de plantilla seguras | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT"
  - "sobrecargas de plantilla seguras"
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Sobrecargas de plantilla seguras
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muchas funciones CRT han quedado obsoletas en favor de nuevas, seguridad\- mejoradas versiones \(por ejemplo, `strcpy_s` es el reemplazo más seguro para `strcpy`\).  CRT proporciona sobrecargas de plantilla para facilitar la transición a las variantes más seguros.  
  
 Por ejemplo, este código genera una advertencia porque está desusada `strcpy` :  
  
 `char szBuf[10];`  
  
 `strcpy(szBuf, "test"); // warning: deprecated`  
  
 Puede omitir la advertencia.  Definir el símbolo `_CRT_SECURE_NO_WARNINGS` para suprimir la advertencia, o para actualizar el código para utilizar `strcpy_s`:  
  
 `char szBuf[10];`  
  
 `strcpy_s(szBuf, 10, "test"); // security-enhanced _s function`  
  
 Las sobrecargas de plantilla proporcionan opciones adicionales.  Definir `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` a sobrecargas de 1 plantilla de CRT estándar funciona de que los variantes más seguros automáticamente.  Si `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` es 1, no hay cambios en el código necesarios.  En segundo plano, la llamada a `strcpy` se cambiará a una llamada a `strcpy_s` con el argumento de tamaño proporcionado automáticamente.  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1`  
  
 `...`  
  
 `char szBuf[10];`  
  
 `strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")`  
  
 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` no afecta a las funciones que toman un recuento, como `strncpy`.  Para habilitar las sobrecargas de plantilla para las funciones de recuento, defina `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` en 1.  Antes de ello, sin embargo, asegúrese de que el código pasa el recuento de caracteres, no el tamaño del búfer \(un error común\).  También, código que explícitamente escribe un terminador nulo al final del búfer después de la llamada de función es innecesaria si el tipo Variant seguro.  Si necesita comportamiento de truncamiento, vea [\_TRUNCATE](../c-runtime-library/truncate.md).  
  
> [!NOTE]
>  `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` macro requiere que `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` también está definido como 1.  Si se define `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` mientras 1 y `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` se define como 0, la aplicación no realizará ninguna sobrecargas de la plantilla.  
  
 La definición de `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` a 1 habilita las sobrecargas de la plantilla de variantes seguros \(nombres que terminen en “\_s”\).  En este caso, si `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` es 1, entonces un pequeño cambio debe crear el código original:  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1`  
  
 `...`  
  
 `char szBuf[10];`  
  
 `strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")`  
  
 Sólo el nombre de la función debe cambiarse \(agrega “\_s”\); la sobrecarga de la plantilla tomará el cuidado para proporcionar el argumento size.  
  
 De forma predeterminada, se definen `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` y `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` como 0 \(deshabilitado\) y `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` se define como 1 \(habilitado\).  
  
 Observe que estas sobrecargas de plantilla solo funcionan para matrices estáticas.  Los búferes dinámicamente asignados requieren cambios adicionales de código fuente.  Visitar de los ejemplos anteriores:  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1`  
  
 `...`  
  
 `char *szBuf = (char*)malloc(10);`  
  
 `strcpy(szBuf, "test"); // still deprecated; have to change to`  
  
 `// strcpy_s(szBuf, 10, "test");`  
  
 Y esto:  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1`  
  
 `...`  
  
 `char *szBuf = (char*)malloc(10);`  
  
 `strcpy_s(szBuf, "test"); // doesn't compile; have to change to`  
  
 `// strcpy_s(szBuf, 10, "test");`  
  
## Vea también  
 [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md)   
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)