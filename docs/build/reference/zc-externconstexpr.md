---
title: /Zc:externConstexpr (variables de constexpr enable extern) | Documentos de Microsoft
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:externConstexpr
dev_langs:
- C++
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cbce8366fdd7be62c8d71f838b298d77849dcdf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/Zc:externConstexpr (variables de habilitar extern constexpr)

El **/Zc:externConstexpr** opción del compilador indica al compilador que se ajusta al estándar de C++ y permitir la vinculación externa para `constexpr` variables. De forma predeterminada, Visual Studio siempre da un `constexpr` variable vinculación interna, incluso si se especifica la `extern` palabra clave.

## <a name="syntax"></a>Sintaxis

> **/Zc:externConstexpr**[**-**]

## <a name="remarks"></a>Comentarios

El **/Zc:externConstexpr** opción del compilador hace que el compilador vinculación externa se aplican a las variables declaradas con `extern constexpr`. En versiones anteriores de Visual Studio y de manera predeterminada o si **/Zc:externConstexpr-** se especifica, Visual Studio aplica vinculación interna a `constexpr` aunque se utilicen variables el `extern` se utiliza la palabra clave. El **/Zc:externConstexpr** opción está disponible a partir de Visual Studio de 2017 actualización 15,6. y está desactivada de forma predeterminada. El [/ permisivo-](permissive-standards-conformance.md) no habilita la opción **/Zc:externConstexpr**.

Si un archivo de encabezado contiene una variable declarada `extern constexpr`, se debe marcar [__declspec (selectany)](../../cpp/selectany.md) para combinar las declaraciones duplicadas en una sola instancia en el archivo binario vinculado. En caso contrario, puede que vea errores del compilador, por ejemplo, LNK2005, para las infracciones de la regla de definición.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para establecer esta opción del compilador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Agregar **/Zc:externConstexpr** o **/Zc:externConstexpr-** a la **opciones adicionales:** panel.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)  
[Auto (palabra clave)](../../cpp/auto-keyword.md)