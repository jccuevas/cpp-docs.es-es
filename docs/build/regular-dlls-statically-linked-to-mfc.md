---
title: Archivos DLL de MFC estándar vinculados estáticamente a MFC
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314785"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>Archivos DLL de MFC estándar vinculados estáticamente a MFC

Un archivo DLL de MFC estándar vinculado estáticamente a MFC es una DLL que usa MFC de forma interna, y las funciones exportadas en el archivo DLL se pueden llamar mediante archivos ejecutables de MFC o no basados en MFC. Como se describe en el nombre, este tipo de archivo DLL se crea con la versión de la biblioteca de vínculos estáticos de MFC. Las funciones se suelen exportar desde un archivo DLL de MFC estándar mediante la interfaz estándar de C. Para obtener un ejemplo de cómo escribir, compilar y usar un archivo DLL de MFC estándar, vea el ejemplo [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).

Tenga en cuenta que el término USRDLL ya no se usa en la documentación de Visual C++. Un archivo DLL de MFC estándar que se vincula estáticamente a MFC tiene las mismas características que el archivo USRDLL anterior.

Un archivo DLL de MFC estándar, vinculado estáticamente a MFC, tiene las características siguientes:

- El ejecutable del cliente se puede escribir en cualquier lenguaje que admita el uso de archivos DLL (C, C++, Pascal, Visual Basic, etc.); no tiene que ser una aplicación MFC.

- El archivo DLL se puede vincular a las mismas bibliotecas de vínculos estáticos de MFC que usan las aplicaciones. Ya no hay una versión independiente de las bibliotecas de vínculos estáticos para las DLL.

- Antes de la versión 4.0 de MFC, USRDLL proporcionaba el mismo tipo de funcionalidad que los archivos DLL de MFC estándar vinculados estáticamente a MFC. A partir de la versión 4.0 de Visual C++, el término USRDLL está obsoleto.

Un archivo DLL de MFC estándar, vinculado estáticamente a MFC, tiene los requisitos siguientes:

- Este tipo de DLL debe crear una instancia de una clase derivada de `CWinApp`.

- Este tipo de DLL usa el elemento `DllMain` proporcionado por MFC. Coloque todo el código de inicialización específico del archivo DLL en la función miembro `InitInstance` y el código de finalización en `ExitInstance`, como en una aplicación MFC estándar.

- Aunque el término USRDLL está obsoleto, todavía debe definir " **_USRDLL**" en la línea de comandos del compilador. Esta definición determina qué declaraciones se extraen de los archivos de encabezado de MFC.

Los archivos DLL de MFC estándar deben tener una clase derivada de `CWinApp` y un solo objeto de esa clase de aplicación, igual que una aplicación MFC. Pero el objeto `CWinApp` del archivo DLL no tiene un suministro de mensajes principal, a diferencia del objeto `CWinApp` de una aplicación.

Tenga en cuenta que el mecanismo `CWinApp::Run` no se aplica a un archivo DLL porque la aplicación es la propietaria del suministro de mensajes principal. Si el archivo DLL abre cuadros de diálogo no modales o tiene una ventana de marco principal propia, el suministro de mensajes principal de la aplicación debe llamar a una rutina exportada por el archivo DLL, que a su vez llama a la función miembro `CWinApp::PreTranslateMessage` del objeto de aplicación del archivo DLL.

Para obtener un ejemplo de esta función, vea el ejemplo DLLScreenCap.

Los símbolos se suelen exportar desde un archivo DLL de MFC estándar mediante la interfaz estándar de C. La declaración de una función exportada desde un archivo DLL de MFC estándar tendría un aspecto similar al siguiente:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Todas las asignaciones de memoria de un archivo DLL de MFC estándar deben permanecer dentro del archivo DLL; el archivo DLL no debe pasar ni recibir ninguno de los elementos siguientes del ejecutable que realiza la llamada:

- Punteros a objetos de MFC

- Punteros a memoria asignada por MFC

Si necesita alguno de estos elementos o tiene que pasar objetos derivados de MFC entre el archivo ejecutable que realiza la llamada y el archivo DLL, tendrá que generar un archivo DLL de extensión de MFC.

Es seguro pasar punteros a la memoria asignada por las bibliotecas en tiempo de ejecución de C entre una aplicación y un archivo DLL solo si realiza una copia de los datos. No debe eliminar ni cambiar el tamaño de estos punteros, ni usarlos sin hacer una copia de la memoria.

Un archivo DLL que se vincula estáticamente a MFC no se puede vincular dinámicamente a los archivos DLL compartidos de MFC. Un archivo DLL vinculado estáticamente a MFC está enlazado de forma dinámica a una aplicación como cualquier otro archivo DLL; las aplicaciones se vinculan como cualquier otro archivo DLL.

Los nombres de las biblioteca de vínculos estáticos de MFC estándar siguen la convención descrita en [Convenciones de nomenclatura para archivos DLL de MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Pero con la versión 3.0 de MFC y versiones posteriores, ya no es necesario especificar manualmente al enlazador la versión de la biblioteca MFC que se quiere vincular. En su lugar, los archivos de encabezado de MFC determinan de forma automática la versión correcta de la biblioteca MFC que se va a vincular en función de las definiciones del preprocesador, como **\_DEBUG** o **_UNICODE**. Los archivos de encabezado de MFC agregan directivas /DEFAULTLIB que indican al enlazador que se vincule en una versión específica de la biblioteca MFC.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Inicialización de archivos DLL de MFC estándar](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Uso de MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Uso de archivos DLL de extensión MFC de base de datos, OLE y Sockets en archivos DLL de MFC estándar](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Creación de un archivo DLL de MFC](../mfc/reference/mfc-dll-wizard.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Archivos DLL de extensión MFC](extension-dlls-overview.md)

## <a name="see-also"></a>Vea también

[Tipos de archivos DLL](kinds-of-dlls.md)
