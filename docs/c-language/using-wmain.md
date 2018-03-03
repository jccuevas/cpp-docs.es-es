---
title: Usar wmain | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- wmain function
ms.assetid: d0300812-adc4-40c6-bba3-b2da25468c80
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 47340642a8c18adfe5e371baca8daca7bd22f28d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-wmain"></a>Usar wmain
**Específicos de Microsoft**  
  
 En el modelo de programación de Unicode, puede definir una versión con caracteres anchos de la función **main**. Utilice **wmain** en lugar de **main** si desea escribir código portable conforme con el modelo de programación Unicode.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
## <a name="remarks"></a>Comentarios  
 Se pueden declarar parámetros formales para **wmain** utilizando un formato similar a **main**. A continuación, se pueden pasar al programa argumentos de caracteres anchos y, opcionalmente, un puntero a entorno de caracteres anchos. Los parámetros `argv` y `envp` de **wmain** son del tipo `wchar_t*`. Por ejemplo:  
  
 Si el programa utiliza una función **main**, el entorno de caracteres multibyte lo crea la biblioteca en tiempo de ejecución durante el inicio del programa. Se crea una copia de caracteres anchos del entorno sólo si es necesario (por ejemplo, por una llamada a las funciones `_wgetenv` o `_wputenv`). En la primera llamada a `_wputenv`, o en la primera llamada a `_wgetenv` si ya existe un entorno MBCS, se crea un entorno correspondiente de cadena de caracteres anchos, y la variable global `_wenviron`, que es una versión con caracteres anchos de la variable global `_environ`, señala a dicho entorno. En este punto, existen dos copias del entorno (MBCS y Unicode) simultáneamente que el sistema operativo mantiene a lo largo de la vida del programa.  
  
 De forma similar, si el programa utiliza una función **wmain**, se crea un entorno de caracteres anchos durante el inicio del programa y la variable global `_wenviron` apunta a dicho entorno. En la primera llamada a `_putenv` o `getenv` se crea un entorno MBCS (ASCII) y la variable global `_environ` apunta a dicho entorno.  
  
 Para obtener más información sobre el entorno MBCS, vea [Internacionalización](../c-runtime-library/internationalization.md) en la *Referencia de la biblioteca en tiempo de ejecución.*  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Función main y ejecución del programa](../c-language/main-function-and-program-execution.md)