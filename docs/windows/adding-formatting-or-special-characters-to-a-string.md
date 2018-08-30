---
title: Agregar formato o caracteres especiales en una cadena | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1b4eda998d598e70fd687276a2d2941d224da4d7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211683"
---
# <a name="adding-formatting-or-special-characters-to-a-string"></a>Agregar formato o caracteres especiales a una cadena

### <a name="to-add-formatting-or-special-characters-to-a-string"></a>Para agregar formato o caracteres especiales en una cadena

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. Seleccione la cadena que desea modificar.

3. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), agregue cualquiera de las secuencias de escape estándar enumerados a continuación para el texto en el **título** cuadro y presione **ENTRAR**.

   |Para obtener esto|Escriba lo siguiente|
   |-----------------|---------------|
   |Nueva línea|\n|
   |Retorno de carro|\r|
   |Tab|\t|
   |Barra diagonal inversa (\\)|\\\|
   |Carácter ASCII|\ddd (notación octal)|
   |alerta (campana)|\a|

> [!NOTE]
> El **cadena** editor no admite el conjunto completo de caracteres ASCII con escape. Solo se pueden usarlos mencionados anteriormente.

Para obtener información sobre cómo agregar recursos a proyectos administrados (aquellos que tienen como destino common language runtime), consulte [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de cadenas](../windows/string-editor.md)  