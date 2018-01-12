---
title: /Zc:externConstexpr (variables de constexpr enable extern) | Documentos de Microsoft
ms.custom: 
ms.date: 9/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Zc:externConstexpr
dev_langs: C++
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 84037e5e8a942d51175d97957d0c05bd6f4aa29d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/Zc:externConstexpr (variables de habilitar extern constexpr)

El **/Zc:externConstexpr** opción del compilador indica al compilador que se ajusta al estándar de C++ y permitir la vinculación externa para `constexpr` variables. De forma predeterminada, Visual Studio siempre da un `constexpr` variable vinculación interna, incluso si se especifica la `extern` palabra clave.

## <a name="syntax"></a>Sintaxis

> /Zc:externConstexpr [-]

## <a name="remarks"></a>Comentarios

El **/Zc:externConstexpr** opción del compilador hace que el compilador vinculación externa se aplican a las variables declaradas con `extern constexpr`. El **/Zc:externConstexpr** opción está disponible a partir de Visual Studio de 2017 actualización 15,5. En versiones anteriores de Visual Studio y de manera predeterminada o si **/Zc:externConstexpr-** se especifica, Visual Studio aplica vinculación interna a `constexpr` aunque se utilicen variables el `extern` se utiliza la palabra clave.

Si un archivo de encabezado contiene una variable declarada `extern constexpr`, se debe marcar [__declspec (selectany)](../../cpp/selectany.md) para combinar las declaraciones duplicadas en una sola instancia en el archivo binario vinculado. En caso contrario, puede que vea errores del compilador, por ejemplo, LNK2005, para las infracciones de la regla de definición.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para establecer esta opción del compilador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. En **propiedades de configuración**, expanda **C/C++** y, a continuación, elija **línea de comandos**.

1. Agregar **/Zc:externConstexpr** o **/Zc:externConstexpr-** a la **opciones adicionales:** panel.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)  
[Auto (palabra clave)](../../cpp/auto-keyword.md)