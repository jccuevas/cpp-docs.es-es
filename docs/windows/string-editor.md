---
title: Editor de cadenas (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string.F1
dev_langs:
- C++
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 02248c7c6f61823649d9643a7321677e23a4afbf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382913"
---
# <a name="string-editor-c"></a>Editor de cadenas (C++)

Una tabla de cadenas es un recurso de Windows que contiene una lista de id., valores y títulos para todas las cadenas de su aplicación. Por ejemplo, los mensajes de la barra de estado se encuentran en la tabla de cadenas.

Al desarrollar una aplicación, puede tener varias tablas de cadenas: una para cada idioma o condición. Sin embargo, un módulo ejecutable solo tiene una tabla de cadenas. Una aplicación en ejecución puede hacer referencia a varias tablas de cadenas si coloca las tablas en varias DLL diferentes.

Las tablas de cadenas facilitan la localización de la aplicación en diferentes idiomas. Si todas las cadenas se encuentran en una tabla de cadenas, puede localizar la aplicación mediante la traducción de las cadenas (y otros recursos) sin cambiar el código fuente. Esto suele ser más deseable que buscar y reemplazar manualmente las distintas cadenas en archivos de código fuente.

Con el editor de cadenas, puede:

- [Buscar una o más cadenas](../windows/finding-a-string.md).

- [Insertar entradas nuevas](../windows/adding-or-deleting-a-string.md) rápidamente en la tabla de cadenas.

- [Mover una cadena de un archivo de recursos a otro](../windows/moving-a-string-from-one-resource-file-to-another.md)

- [Usar la edición en contexto para las propiedades ID, Value y Caption](../windows/changing-the-properties-of-a-string.md) y ver los cambios inmediatamente.

- [Cambiar la propiedad caption de varias cadenas](../windows/changing-the-caption-property-of-multiple-strings.md)

- [Agregar formato o caracteres especiales a una cadena](../windows/adding-formatting-or-special-characters-to-a-string.md)

   > [!NOTE]
   > Windows no permite la creación de tablas de cadenas vacías. Si crea una tabla de cadenas sin entradas, se elimina automáticamente al guardar el archivo de recursos.

Para obtener información sobre cómo agregar recursos a proyectos administrados (aquellos que tienen como destino common language runtime), consulte [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Cadenas](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[Acerca de las cadenas](/windows/desktop/menurc/about-strings)

