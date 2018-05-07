---
title: Páginas de códigos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.international
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fc272d02fee38b3a260a5b6bb6330f4f6a5eb362
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="code-pages"></a>Páginas de códigos

Una *página de códigos* es un juego de caracteres, que puede incluir números, signos de puntuación y otros glifos. Idiomas y configuraciones regionales distintas pueden usar páginas de códigos distintas. Por ejemplo, la página de códigos ANSI 1252 se usa para el inglés y para la mayoría de idiomas europeos, mientras que la página de códigos OEM 932 se usa para los caracteres Kanji del japonés.

 Una página de códigos puede representarse en una tabla como una asignación de caracteres para valores multibyte o de un solo byte. Muchas páginas de códigos comparten el juego de caracteres ASCII para los caracteres que están en el intervalo de 0x00 a 0x7F.

 La biblioteca en tiempo de ejecución de Microsoft usa los siguientes tipos de páginas de códigos:

- Página de códigos ANSI predeterminada del sistema. De manera predeterminada, al iniciar el sistema en tiempo de ejecución se establece automáticamente la página de códigos multibyte en la página de códigos ANSI predeterminada del sistema, que se obtiene del sistema operativo. La llamada:

    ```C
    setlocale ( LC_ALL, "" );
    ```

     también establece la configuración regional a la página de códigos ANSI predeterminada del sistema.

- Página de códigos de configuración regional. El comportamiento de un número de rutinas en tiempo de ejecución depende de la configuración regional actual, que incluye la página de códigos de esta. (Para obtener más información, vea [Locale-Dependent Routines](../c-runtime-library/locale.md) [Rutinas dependientes de la configuración regional]). De manera predeterminada, todas las rutinas dependientes de la configuración regional en la biblioteca en tiempo de ejecución de Microsoft usan la página de códigos que corresponde a la configuración regional "C". En tiempo de ejecución, puede cambiar o consultar la página de códigos de la configuración regional en uso con una llamada a [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

- Página de códigos multibyte. El comportamiento de la mayoría de las rutinas de caracteres multibyte en la biblioteca en tiempo de ejecución depende de la configuración de la página de códigos multibyte actual. De manera predeterminada, estas rutinas usan la página de códigos ANSI predeterminada del sistema. En tiempo de ejecución, puede cambiar o consultar la página de códigos multibyte con [_getmbcp](../c-runtime-library/reference/getmbcp.md) y [_setmbcp](../c-runtime-library/reference/setmbcp.md), respectivamente.

- La configuración regional "C" se define mediante ANSI para que coincida con la configuración regional en la que se han ejecutado tradicionalmente los programas de C. La página de códigos para la configuración regional "C" (página de códigos "C") corresponde al juego de caracteres ASCII. Por ejemplo, en la configuración regional "C", **islower** devuelve true solo para los valores de 0x61 a 0x7A. En otra configuración regional, **islower** puede devolver true para estos así como para otros valores, como se define mediante esa configuración regional.

## <a name="see-also"></a>Vea también

[Internacionalización](../c-runtime-library/internationalization.md)<br/>
 [Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>