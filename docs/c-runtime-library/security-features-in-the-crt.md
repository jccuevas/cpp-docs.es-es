---
title: Características de seguridad de CRT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- security deprecation warnings [C++]
- CRT_NONSTDC_NO_DEPRECATE
- buffers [C++], buffer overruns
- deprecation warnings (security-related), disabling
- _CRT_NONSTDC_NO_WARNINGS
- security [CRT]
- _CRT_SECURE_NO_WARNINGS
- _CRT_NONSTDC_NO_DEPRECATE
- _CRT_SECURE_NO_DEPRECATE
- security-enhanced CRT
- CRT_SECURE_NO_WARNINGS
- CRT_SECURE_NO_DEPRECATE
- deprecation warnings (security-related)
- buffer overruns
- CRT_NONSTDC_NO_WARNINGS
- CRT, security enhancements
- parameters [C++], validation
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8195e9a7e37ac9fa9186118889d7717698d2b784
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="security-features-in-the-crt"></a>Características de seguridad de CRT
Muchas funciones anteriores de CRT tienen versiones nuevas y más seguras. Si existe una función segura, la versión anterior y menos segura está marcada como desusada y la nueva versión presenta el sufijo `_s` ("segura").  
  
 En este contexto, "en desuso" simplemente significa que no se recomienda el uso de una función; no indica que esté programada la retirada de la función de CRT.  
  
 Las funciones seguras no evitan ni corrigen errores de seguridad, sino que los detectan cuando ocurren. Realizan comprobaciones adicionales de condiciones de error y, en caso de que se detecte algún error, invocan a un controlador de errores (vea [Validación de errores](../c-runtime-library/parameter-validation.md)).  
  
 Por ejemplo, la función `strcpy` no tiene ninguna manera de indicar si la cadena que se está copiando es demasiado grande para su búfer de destino. Sin embargo, su equivalente seguro, `strcpy_s`, adopta el tamaño del búfer como un parámetro, lo que le permite determinar si se producirá una saturación del búfer. Si usa `strcpy_s` para copiar once caracteres en un búfer de diez caracteres, se trata de un error por parte del usuario; `strcpy_s` no puede corregir este error, pero puede detectarlo e informar para que se invoque al controlador de parámetros no válidos.  
  
## <a name="eliminating-deprecation-warnings"></a>Eliminación de advertencias sobre desuso  
 Hay varias maneras de eliminar las advertencias sobre desuso de las funciones más antiguas y menos seguras. La más sencilla consiste simplemente en definir `_CRT_SECURE_NO_WARNINGS` o en usar el pragma [warning](../preprocessor/warning.md). De esta forma, se deshabilitan las advertencias sobre desuso, pero persistirán los errores de seguridad que ocasionaron las advertencias. Es mucho más conveniente dejar habilitadas las advertencias sobre desuso y beneficiarse de las nuevas características de seguridad de CRT.  
  
 En C++, la manera más fácil de hacerlo es usar las [sobrecargas de plantillas seguras](../c-runtime-library/secure-template-overloads.md), que en muchos casos eliminarán las advertencias sobre desuso reemplazando las llamadas a funciones en desuso por llamadas a las nuevas versiones seguras de estas funciones. Por ejemplo, considere esta llamada en desuso a `strcpy`:  
  
```  
char szBuf[10];   
strcpy(szBuf, "test"); // warning: deprecated   
```  
  
 Al definir `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` como 1, se elimina la advertencia cambiando la llamada a `strcpy` por `strcpy_s`, lo que evita las saturaciones del búfer. Para obtener más información, consulta [Secure Template Overloads](../c-runtime-library/secure-template-overloads.md).  
  
 En el caso de estas funciones en desuso sin sobrecargas de plantillas seguras, debe considerar en última instancia actualizar manualmente el código para usar las versiones seguras.  
  
 Otro origen de las advertencias sobre desuso, no relacionadas con la seguridad, son las funciones POSIX. Reemplace los nombres de funciones POSIX por sus equivalentes estándar (por ejemplo, cambie [access](../c-runtime-library/reference/access-crt.md) por [_access](../c-runtime-library/reference/access-waccess.md)), o bien deshabilite las advertencias sobre desuso relacionadas con POSIX mediante la definición de `_CRT_NONSTDC_NO_WARNINGS`. Para obtener más información, consulte [Compatibilidad](compatibility.md).  
  
## <a name="additional-security-features"></a>Características de seguridad adicionales  
 Entre las características de seguridad, se incluyen las siguientes:  
  
-   `Parameter Validation`. Se validan los parámetros transferidos a las funciones de CRT, tanto en las funciones seguras como en muchas versiones preexistentes de las funciones. Estas validaciones incluyen:  
  
    -   Comprobar los valores **NULL** que se pasan a las funciones.  
  
    -   Comprobar la validez de los valores enumerados.  
  
    -   Comprobar si los valores de enteros se encuentran en intervalos válidos.  
  
-   Para más información, consulte [Validación de parámetros](../c-runtime-library/parameter-validation.md).  
  
-   El desarrollador también puede acceder a un controlar de parámetros no válidos. Al detectar un parámetro no válido, en lugar de validar la aplicación y cerrarla, CRT ofrece una forma de comprobar estos problemas con la función [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).  
  
-   `Sized Buffers`. Las funciones seguras requieren que el tamaño del búfer se transfiera a cualquier función que escribe en un búfer. Las versiones seguras validan que el búfer es suficientemente grande antes de escribir en él, de tal forma que se evitan así errores peligrosos de saturación del búfer que podrían permitir la ejecución de código malintencionado. Estas funciones suelen devolver un tipo `errno` de código de error e invocar al controlador de parámetros no válidos si el tamaño del búfer es demasiado pequeño. Las funciones que leen de los búferes de entrada, como `gets`, tienen versiones seguras que requieren que se especifique un tamaño máximo.  
  
-   `Null termination`. Algunas funciones que dejan cadenas potencialmente sin terminar tienen versiones seguras que garantizan que las cadenas se terminan correctamente en NULL.  
  
-   `Enhanced error reporting`. Las funciones seguras devuelven códigos de error con más información sobre el error de la que estaba disponible con las funciones preexistentes. Las funciones seguras y muchas de las funciones preexistentes ahora establecen `errno` y también suelen devolver un tipo de código `errno`, a fin de ofrecer más información sobre los errores.  
  
-   `Filesystem security`. Las API de E/S de archivo seguras admiten el acceso seguro a los archivos de forma predeterminada.  
  
-   `Windows security`. Las API de proceso seguras aplican directivas de seguridad y permiten especificar ACL.  
  
-   `Format string syntax checking`. Se detectan cadenas no válidas, por ejemplo, con el uso de caracteres de campo de tipo incorrecto en las cadenas de formato `printf`.  
  
## <a name="see-also"></a>Vea también  
 [Validación de parámetros](../c-runtime-library/parameter-validation.md)   
 [Sobrecargas de plantillas seguras](../c-runtime-library/secure-template-overloads.md)   
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)