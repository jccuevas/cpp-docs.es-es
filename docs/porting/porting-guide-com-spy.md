---
title: "Guía de migración: COM Spy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b3473d7cd4ec23749f95bd06a1d993abc3209df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="porting-guide-com-spy"></a>Guía de migración: COM Spy
Este tema es el segundo de una serie de artículos que demuestra el proceso de actualización de antiguos proyectos de Visual C++ a la versión más reciente de Visual Studio. El código de ejemplo que se muestra en este tema se compiló por última vez con Visual Studio 2005.  
  
## <a name="comspy"></a>COMSpy  
 COMSpy es un programa que supervisa y registra la actividad de los componentes con servicio en un equipo. Los componentes con servicio son componentes COM+ que se ejecutan en un sistema y pueden ser usados por los equipos de la misma red. Los administra la funcionalidad Servicios de componentes que se encuentra en el Panel de control de Windows.  
  
### <a name="step-1-converting-the-project-file"></a>Paso 1. Convertir el archivo del proyecto.  
 El archivo del proyecto se convierte fácilmente y genera un informe de migración. Existen unas pocas entradas en el informe que nos informan sobre los problemas que puede que debamos tratar de resolver. Este es un problema notificado (tenga en cuenta que a lo largo de este tema los mensajes de error a veces se acortan para que sean más fáciles de leer, por ejemplo, quitando las rutas de acceso completas):  
  
```Output  
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).  
```  
  
 Uno de los problemas frecuentes al actualizar proyectos es que quizás sea necesario revisar la configuración del OutputFile del vinculador en el cuadro de diálogo de propiedades del proyecto. Para los proyectos anteriores a Visual Studio 2010, OutputFile es un ajuste con el que tiene problemas el asistente de conversión automática si se establece en un valor no estándar. En este caso, las rutas de acceso de los archivos de salida se establecieron en una carpeta no estándar, XP32_DEBUG. Para obtener más información sobre este error, consultamos una [entrada de blog](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx) relacionada con la actualización de proyectos de Visual C++ 2010, que fue la actualización en la que se pasó de vcbuild a msbuild, un cambio significativo. Según esta información, el valor predeterminado del ajuste OutputFile cuando se crea un nuevo proyecto es $(OutDir)$(TargetName)$(TargetExt), pero este no se establece durante la conversión, ya que no es posible que los proyectos convertidos comprueben que todo sea correcto.  Sin embargo, vamos a intentar colocarlo en OutputFile y ver si funciona.  Sí que funciona, de modo que podemos continuar. Si no hay ninguna razón específica para utilizar una carpeta de salida no estándar, se recomienda utilizar la ubicación estándar. En este caso, hemos optado por dejar la ubicación de salida como la no estándar durante el proceso de migración y actualización; $(OutDir) se resuelve en la carpeta XP32_DEBUG en la configuración de Debug y la carpeta ReleaseU para la configuración de Release.  
  
### <a name="step-2-getting-it-to-build"></a>Paso 2. Hacer que compile  
 Al compilar el proyecto migrado, se producen varios errores y advertencias.  
  
 ComSpyCtl no compila debido a este error del compilador:  
  
```Output  
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled  
```  
  
 El error hace referencia al método Save en la clase IPersistStreamInitImpl en atlcom.h.  
  
```cpp  
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)  
{  
     T* pT = static_cast<T*>(this);  
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));  
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());  
}  
```  
  
 El problema es que una conversión que aceptó una versión anterior del compilador ya no es válida. Con el fin de cumplir con el estándar de C++, parte del código que anteriormente se permitía ya no se permite. En este caso no es seguro pasar un puntero no const a una función que espera un puntero const.  La solución es encontrar la declaración de IPersistStreamInit_Save en la clase CComSpy y agregar el modificador const al tercer parámetro.  
  
```cpp  
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)  
  
```  
  
 Y realizar un cambio parecido en IPersistStreamInit_Load.  
  
```cpp  
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);  
```  
  
 El siguiente error está relacionado con el registro.  
  
```Output  
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.  
```  
  
 Ya no necesitamos este comando de registro post-compilación. En su lugar, simplemente eliminamos el comando de compilación personalizada y especificamos en la configuración del vinculador que se registre la salida.  
  
### <a name="dealing-with-warnings"></a>Gestionar advertencias  
 El proyecto genera la siguiente advertencia del vinculador.  
  
```Output  
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification  
```  
  
 La opción del compilador /SAFESEH no es útil en el modo de depuración, que es cuando /EDITANDCONTINUE es útil, por lo que la solución aquí consiste en deshabilitar/SAFESEH únicamente para configuraciones de Debug. Para hacer esto en el diálogo de propiedades, abrimos el diálogo de propiedades del proyecto que genera este error y establecemos primero la Configuración de depuración (en realidad Depurar Unicode) y, a continuación, en la sección avanzada del vinculador, restablecemos la propiedad La imagen tiene controladores de excepciones seguros en No (/ SAFESEH:NO).  
  
 El compilador nos advierte de que PROP_ENTRY_EX está en desuso. No es seguro y el sustituto recomendado es PROP_ENTRY_TYPE_EX.  
  
```cpp  
BEGIN_PROPERTY_MAP(CComSpy)  
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_PAGE(CLSID_StockFontPage)  
END_PROPERTY_MAP()  
```  
  
 Cambiamos el código de ccomspy.h según corresponda, agregando los tipos COM que sean necesarios.  
  
```cpp  
BEGIN_PROPERTY_MAP(CComSpy)  
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)  
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)  
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)  
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)  
     PROP_PAGE(CLSID_StockFontPage)  
END_PROPERTY_MAP()  
```  
  
 Ya estamos llegando a las últimas advertencias, que también se han producido debido a comprobaciones más estrictas de cumplimiento del compilador:  
  
```Output  
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'  
```  
  
 La advertencia C4018 procede de este código:  
  
```cpp  
for (i=0;i<lCount;i++)  
    CoTaskMemFree(pKeys[i]);  
```  
  
 El problema es que i se declara como UINT y lCount se declara como long, de ahí que signed/unsigned no coincidan. Sería conveniente cambiar el tipo de lCount a UINT, dado que obtiene su valor de IMtsEventInfo::get_Count, que utiliza el tipo long y no está en el código de usuario. De modo que agregamos una conversión al código. Una conversión de estilo C serviría para una conversión numérica como esta, pero static_cast es el estilo recomendado.  
  
```cpp  
for (i=0;i<static_cast<UINT>(lCount);i++)  
    CoTaskMemFree(pKeys[i]);  
```  
  
 Esas advertencias son casos en los que se declaró una variable en una función que tiene un parámetro con el mismo nombre, lo que genera un código que podría dar lugar a confusiones. Lo solucionamos cambiando los nombres de las variables locales.  
  
### <a name="step-3-testing-and-debugging"></a>Paso 3. Pruebas y depuración  
 Probamos la aplicación en primer lugar ejecutando los distintos menús y comandos y cerrando a continuación la aplicación. El único problema que se observó fue una aserción de depuración al cerrar la aplicación. El problema apareció en el destructor de CWindowImpl, una clase base del objeto CSpyCon, el componente COM principal de la aplicación. El error de aserción se produjo en el siguiente código en atlwin.h.  
  
```cpp  
virtual ~CWindowImplRoot()  
{  
     #ifdef _DEBUG  
     if(m_hWnd != NULL)// should be cleared in WindowProc  
     {  
          ATLTRACE(atlTraceWindowing, 0, _T("ERROR - Object deleted before window was destroyed\n"));  
          ATLASSERT(FALSE);  
     }  
     #endif //_DEBUG  
}  
```  
  
 El valor de hWnd normalmente se establece en cero en la función WindowProc, pero eso no sucedió porque en lugar del WindowProc predeterminado, se llamó a un controlador personalizado para el mensaje de Windows (WM_SYSCOMMAND) que cierra la ventana. El controlador personalizado no establecía en cero el valor de hWnd. Al echar un vistazo al código similar de la clase CWnd de MFC, se ve que cuando se destruye una ventana, se llama a OnNcDestroy, y en la documentación de MFC se aconseja que al reemplazar CWnd::OnNcDestroy, se llame al NcDestroy de base para asegurarse de que tengan lugar las operaciones de limpieza adecuadas, incluida la separación del identificador de la ventana de la propia ventana, o en otras palabras, que se establezca el valor de hWnd en cero. Esta aserción también se podría haber activado en la versión original del ejemplo, puesto que el mismo código de aserción estaba presente en la versión anterior de atlwin.h.  
  
 Para probar la funcionalidad de la aplicación, creamos un componente con servicio mediante la plantilla de proyecto de ATL y decidimos agregar compatibilidad con COM+ en el asistente para proyectos de ATL. Si no ha trabajado antes con componentes con servicio, no es difícil crear uno, registrarlo y ponerlo a disposición de otras aplicaciones en el sistema o red. La aplicación COM Spy está diseñada para supervisar la actividad de los componentes con servicio como ayuda para el diagnóstico.  
  
 A continuación agregamos una clase, elegimos Objeto ATL y especificamos el nombre del objeto como Dog. A continuación, en dog.h y dog.cpp, agregamos la implementación.  
  
```cpp  
STDMETHODIMP CDog::Wag(LONG* lDuration)  
{  
    // TODO: Add your implementation code here  
    *lDuration = 100l;  
    return S_OK;  
}  
```  
  
 A continuación, llevamos a cabo la compilación y el registro (deberá ejecutar Visual Studio como Administrador) y la activación mediante la aplicación Componente con servicio del Panel de control de Windows. Creamos un proyecto de Windows Forms de C#, arrastramos un botón al formulario desde el cuadro de herramientas e hicimos doble clic en un controlador de eventos de Click. Agregamos el siguiente código para crear una instancia del componente Dog.  
  
```cpp  
private void button1_Click(object sender, EventArgs e)  
{  
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();  
    dog1.Wag();  
}  
```  
  
 Este se ejecutó sin problemas y con COM Spy ejecutándose y configurado para supervisar el componente Dog, aparecen grandes cantidades de datos que muestran la actividad.  
  
## <a name="see-also"></a>Vea también  
 [Migración y actualización: ejemplos y casos prácticos](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [Ejemplo siguiente: Spy++](../porting/porting-guide-spy-increment.md)   
 [Ejemplo anterior: Scribble de MFC](../porting/porting-guide-mfc-scribble.md)