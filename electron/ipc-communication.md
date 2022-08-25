## IPC communication explained in simple way with practical examples

### Renderer -> main - no return value

Main:
```
ipcMain.on('set-title', handleSetTitle);
```

Renderer (preload.js):
```
contextBridge.exposeInMainWorld('electronAPI', {
  setTitle: (title) => ipcRenderer.send('set-title', title)
});
```

### Renderer -> main - with return value

Main:
```
ipcMain.handle('dialog:openFile', () => {
  const { canceled, filePaths } = await dialog.showOpenDialog();
  if (canceled) {
    return;
  } else {
    return filePaths[0]; // sends data to renderer
  }
});
```

Renderer (preload.js):
```
contextBridge.exposeInMainWorld('electronAPI', {
  openFile: () => ipcRenderer.invoke('dialog:openFile')
});
```

### Main -> renderer

Main:
```
mainWindow.webContents.send('update-active-users-count', activeUsersCount);
```

Renderer (preload.js):
```
contextBridge.exposeInMainWorld('electronAPI', {
  onUpdateActiveUsersCount: (callback) => ipcRenderer.on('update-active-users-count', callback)
});
```

