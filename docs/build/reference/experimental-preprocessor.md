---
title: '/experimental: preprocesador (habilitar el modo de cumplimiento del preprocesador)'
description: 'Use la opción del compilador/experimental: preprocesador para habilitar la compatibilidad experimental del compilador para un preprocesador compatible con el estándar.'
ms.date: 10/31/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: cb1ac63d2c12083975139455d8625544cb419adf
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754043"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/experimental: preprocesador (habilitar el modo de cumplimiento del preprocesador)

Esta opción habilita un preprocesador experimental basado en tokens que se ajusta mejor a los estándares de C++ 11, incluidas las características del preprocesador de C99. Para obtener más información, vea [información general del preprocesador experimental de MSVC](../../preprocessor/preprocessor-experimental-overview.md).

## <a name="syntax"></a>Sintaxis

> **/experimental: preprocesador**[ **-** ]

## <a name="remarks"></a>Comentarios

Use la opción del compilador **/experimental: preprocesador** para habilitar el preprocesador compatible con experimental. Puede usar **/experimental: preprocesser-** Option para especificar explícitamente el preprocesador tradicional.

La opción **/experimental: preprocesador** está disponible a partir de la versión 15,8 de Visual Studio 2017.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **C /C++**  > **Línea de comandos**.

1. Modifique la propiedad **opciones adicionales** para incluir **/experimental: preprocesador** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](zc-conformance.md)
