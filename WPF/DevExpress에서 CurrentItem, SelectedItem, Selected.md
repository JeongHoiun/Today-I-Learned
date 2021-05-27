# DevExpress에서 CurrentItem, SelectedItem, SelectedItems의 차이

Created: May 24, 2021 4:30 PM
Tags: DevExpress

## 발단

- `Multi-row Select` 화면을 개발하다 해당 화면이 `Single-row select`로 바뀜
- `Single-row select`로 바뀌면서 해당 `GridControl` 의 property는 `SelectedItems`에서 `SelectedItem`으로 바뀜
- 이와중에 선택을 변경하는 이벤트를 `SelectionChanged`를 사용하고 있음
- `SelectionChanged` 이벤트는 SelectedItems의 변경을 보고 있음

## 그래서 차이는?

### CurrentItem

- 현재 포커싱 된 아이템을 바인딩
- `SelectionMode`가 `MultiRow`인 경우 가장 최근에 포커싱 된 아이템

```xml
<dxg:GridControl x:Name="ModuleViewGridControl"
                             Margin="10,0,10,0"
                             Grid.Row="1"
                             ItemsSource="{Binding Modules, IsAsync=True}"
                             CurrentItem="{Binding SelectedModule}"
                             VerticalAlignment="Stretch"
                             SelectionMode="None"
                             IsEnabled="{Binding ComponentEnable}">
                <i:Interaction.Triggers>
                    <i:EventTrigger EventName="CurrentItemChanged">
                        <prism:InvokeCommandAction Command="{Binding SelectedModuleChangedCommand}">
                        </prism:InvokeCommandAction>
                    </i:EventTrigger>
                </i:Interaction.Triggers>
</dxg:GridControl>
```

### SelectedItem

- 현재 포커싱 된 아이템을 바인딩
- `SelectionMode`가 `MultiRow`인 경우 가장 처음에 포커싱 된 아이템

```xml
<dxg:GridControl x:Name="ModuleViewGridControl"
                             Margin="10,0,10,0"
                             Grid.Row="1"
                             ItemsSource="{Binding Modules, IsAsync=True}"
                             SelectedItem="{Binding SelectedModule}"
                             VerticalAlignment="Stretch"
                             SelectionMode="None"
                             IsEnabled="{Binding ComponentEnable}">
                <i:Interaction.Triggers>
                    <i:EventTrigger EventName="SelectedItemChanged">
                        <prism:InvokeCommandAction Command="{Binding SelectedModuleChangedCommand}">
                        </prism:InvokeCommandAction>
                    </i:EventTrigger>
                </i:Interaction.Triggers>
</dxg:GridControl>
```

### SelectedItems

- 현재 포커싱 된 아이템들의 묶음

```xml
<dxg:GridControl x:Name="ModuleViewGridControl"
                             Margin="10,0,10,0"
                             Grid.Row="1"
                             ItemsSource="{Binding Modules, IsAsync=True}"
                             SelectedItems="{Binding SelectedModule}"
                             VerticalAlignment="Stretch"
                             SelectionMode="None"
                             IsEnabled="{Binding ComponentEnable}">
                <i:Interaction.Triggers>
                    <i:EventTrigger EventName="SelectionChanged">
                        <prism:InvokeCommandAction Command="{Binding SelectedModuleChangedCommand}">
                        </prism:InvokeCommandAction>
                    </i:EventTrigger>
                </i:Interaction.Triggers>
</dxg:GridControl>
```

## 참고

- [https://docs.devexpress.com/WPF/DevExpress.Xpf.Grid.DataControlBase.CurrentItem](https://docs.devexpress.com/WPF/DevExpress.Xpf.Grid.DataControlBase.CurrentItem)
- [https://docs.devexpress.com/WPF/DevExpress.Xpf.Grid.DataControlBase.SelectedItem](https://docs.devexpress.com/WPF/DevExpress.Xpf.Grid.DataControlBase.SelectedItem)
- [https://docs.devexpress.com/WPF/DevExpress.Xpf.Grid.DataControlBase.SelectedItems](https://docs.devexpress.com/WPF/DevExpress.Xpf.Grid.DataControlBase.SelectedItems)