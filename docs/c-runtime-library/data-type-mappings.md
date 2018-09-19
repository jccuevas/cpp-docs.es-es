---
title: Asignaciones de tipos de datos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _TXCHAR
- _TUCHAR
- _TINT
- _TSCHAR
- _TCHAR
- TCHAR::H
- TCHAR
- _T
- _TEXT
dev_langs:
- C++
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- TXCHAR type
- _TSCHAR type
- T type
- _TUCHAR type
- _TEXT type
- _T type
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d11f6fd60cb85406f729fc337054858fbed73f3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100488"
---
# <a name="data-type-mappings"></a>Asignaciones de tipos de datos

Estas asignaciones de tipo de datos se definen en TCHAR.H y dependen de que la constante `_UNICODE` o `_MBCS` se haya definido en el programa.

Para obtener información al respecto, vea [Utilizar tipos de datos de TCHAR.H con código _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md).

### <a name="generic-text-data-type-mappings"></a>Asignaciones de tipos de datos de texto genérico

|Texto genérico<br /><br /> nombre de tipo de datos|SBCS (_UNICODE,<br /><br /> _MBCS no<br /><br /> definidos)|_MBCS<br /><br /> definición|_UNICODE<br /><br /> definición|
|--------------------------------------|----------------------------------------------------|------------------------|---------------------------|
|`_TCHAR`|`char`|`char`|`wchar_t`|
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|
|`_TINT`|`int`|`int`|`wint_t`|
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|
|`_T` o `_TEXT`|Sin efecto (quitado por el preprocesador)|Sin efecto (quitado por el preprocesador)|`L` (convierte el carácter o la cadena siguiente en su equivalente de Unicode)|

## <a name="see-also"></a>Vea también

[Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md)<br/>
[Asignaciones de constantes y de variables globales](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[Asignaciones de rutinas](../c-runtime-library/routine-mappings.md)<br/>
[Ejemplo de programa de texto genérico](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[Usar asignaciones de texto genérico](../c-runtime-library/using-generic-text-mappings.md)