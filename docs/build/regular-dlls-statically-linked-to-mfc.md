---
title: Archivos DLL MFC estándar vinculadas estáticamente a MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
ms.openlocfilehash: 1f05b5e3c268935cf3161fb7184e04b3e3ea1446
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314785"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>Archivos DLL MFC estándar vinculadas estáticamente a MFC

Normal que MFC DLL vinculado estáticamente a MFC es un archivo DLL utiliza MFC internamente y las funciones exportadas en el archivo DLL se pueden llamar desde archivos ejecutables MFC o no MFC. Como se describe en el nombre, este tipo de archivo DLL se compila con la versión de la biblioteca de vínculos estáticos de MFC. Las funciones se suelen exportar desde DLL de MFC mediante la interfaz estándar de C normal. Para obtener un ejemplo de cómo escribir, crear y usar un archivo DLL MFC, vea el ejemplo [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).

Tenga en cuenta que el término USRDLL ya no se usa en la documentación de Visual C++. DLL MFC estándar que se vincula estáticamente a MFC tiene las mismas características que el archivo USRDLL anterior.

Una DLL de MFC regular, vinculados estáticamente a MFC, tiene las siguientes características:

- El archivo ejecutable del cliente puede escribirse en cualquier lenguaje que admite el uso de archivos DLL (C, C++, Pascal, Visual Basic y así sucesivamente); no tiene que ser una aplicación MFC.

- Puede vincular el archivo DLL a las mismas bibliotecas de vínculos estáticos de MFC utilizadas las aplicaciones. Ya no es una versión independiente de las bibliotecas de vínculos estáticos para archivos DLL.

- Antes de la versión 4.0 de MFC, USRDLL proporciona el mismo tipo de funcionalidad como archivos DLL de MFC estándar vinculados estáticamente a MFC. A partir de Visual C++ versión 4.0, el término USRDLL está obsoleta.

Una DLL de MFC regular, vinculados estáticamente a MFC, tiene los siguientes requisitos:

- Este tipo de archivo DLL debe crear una instancia de una clase derivada de `CWinApp`.

- Este tipo de archivo DLL utiliza la `DllMain` proporcionadas por MFC. Colocar todo código de inicialización específica para DLL el `InitInstance` código de función y de finalización de miembros en `ExitInstance` como en una aplicación MFC normal.

- Aunque el término USRDLL está obsoleta, debe definir "**_USRDLL**" en la línea de comandos del compilador. Esta definición determina las declaraciones que se van a extraer de los archivos de encabezado MFC.

Archivos DLL de MFC estándar debe tener un `CWinApp`-derivados de clase y un único objeto de esa clase de aplicación, como una aplicación MFC. Sin embargo, el `CWinApp` objeto del archivo DLL no tiene un suministro de mensajes principal, como hace el `CWinApp` objeto de una aplicación.

Tenga en cuenta que el `CWinApp::Run` mecanismo no se aplica a un archivo DLL, porque la aplicación es propietaria del suministro de mensajes principal. Si el archivo DLL abre los cuadros de diálogo no modales o tiene una ventana de marco principal de su propio, el bombeo de mensajes principal de la aplicación debe llamar a una rutina exportada por el archivo DLL que a su vez llama a la `CWinApp::PreTranslateMessage` la función miembro de la DLL objeto de aplicación.

Para obtener un ejemplo de esta función, vea el ejemplo DLLScreenCap.

Símbolos normalmente se exportan desde la DLL de MFC mediante la interfaz estándar de C normal. La declaración de una función exportada desde un archivo DLL MFC sería algo parecido a esto:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Todas las asignaciones de memoria dentro de un archivo DLL MFC deben permanecer dentro de la DLL; el archivo DLL no debe pasar a o recibir desde el archivo ejecutable de llamada cualquiera de las siguientes acciones:

- Punteros a objetos MFC

- Punteros a la memoria asignada por MFC

Si necesita realizar cualquiera de los pasos anteriores como si necesita pasar objetos derivados de MFC entre el archivo ejecutable de llamada y el archivo DLL, debe crear un archivo DLL de extensión MFC.

Es seguro pasar punteros a la memoria asignados por las bibliotecas de tiempo de ejecución de C entre una aplicación y un archivo DLL solo si realiza una copia de los datos. No debe eliminar o cambiar el tamaño de estos punteros o usarlos sin tener que realizar una copia de la memoria.

Un archivo DLL que se vincula estáticamente a MFC también dinámicamente no se puede vincular a archivos DLL de MFC compartido. Un archivo DLL que se vincula estáticamente a MFC se enlacen dinámicamente a una aplicación, al igual que cualquier otro archivo DLL; al igual que cualquier otro archivo DLL, aplicaciones de vínculo a él.

Las bibliotecas de vínculos estáticos de MFC estándar se nombran según la convención descrita en [convenciones de nomenclatura para archivos DLL de MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Sin embargo, con la versión 3.0 y versiones posterior de MFC, ya no es necesario especificar manualmente al vinculador la versión de la biblioteca MFC que desea vincular. En su lugar, los archivos de encabezado MFC determinan automáticamente la versión correcta de la biblioteca MFC debe vincular en preprocesador según define, como  **\_depurar** o **_UNICODE**. Los archivos de encabezado MFC agregan directivas DEFAULTLIB indica al vinculador para vincular en una versión específica de la biblioteca MFC.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Inicializar archivos DLL de MFC estándar](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Usar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Uso de archivos DLL de extensión MFC de base de datos, OLE y Sockets en archivos DLL de MFC estándar](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Creación de una DLL de MFC](../mfc/reference/mfc-dll-wizard.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Archivos DLL de extensión MFC](extension-dlls-overview.md)

## <a name="see-also"></a>Vea también

[Tipos de archivos DLL](kinds-of-dlls.md)
