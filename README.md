<Window x:Class="WpfApplication1.MainWindow"

    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"

    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"

    Title="MainWindow">

    <Grid>

        <Viewport3D>

            <Viewport3D.Camera>

                <PerspectiveCamera Position="0,0,5"/>

            </Viewport3D.Camera>

            <ModelVisual3D>

                <ModelVisual3D.Content>

                    <GeometryModel3D>

                        <GeometryModel3D.Geometry>

                            <MeshGeometry3D Positions="-1,-0.5,-0.05 1,-0.5,-0.05 1,0.5,-0.05 -1,0.5,-0.05 -1,-0.5,0.05 1,-0.5,0.05 1,0.5,0.05 -1,0.5,0.05"

                                            TriangleIndices="0 1 2 2 3 0 1 5 6 6 2 1 5 4 7 7 6 5 4 0 3 3 7 4 3 2 6 6 7 3 4 5 1 1 0 4"

                                            TextureCoordinates="0,0 1,0 1,1 0,1 0,0 1,0 1,1 0,1"/>

                        </GeometryModel3D.Geometry>

                        <GeometryModel3D.Material>

                            <DiffuseMaterial>

                                <DiffuseMaterial.Brush>

                                    <SolidColorBrush Color="White"/>

                                </DiffuseMaterial.Brush>

                            </DiffuseMaterial>

                        </GeometryModel3D.Material>

                    </GeometryModel3D>

                </ModelVisual3D.Content>

                <ModelVisual3D.Transform>

                    <ScaleTransform3D ScaleX="2" ScaleY="1" ScaleZ="0.1"/>

                </ModelVisual3D.Transform>

            </ModelVisual3D>

            <ModelVisual3D>

                <ModelVisual3D.Content>

                    <AmbientLight Color="#666666"/>

                </ModelVisual3D.Content>

            </ModelVisual3D>

            <ModelVisual3D>

                <ModelVisual3D.Content>

                    <DirectionalLight Color="White" Direction="-1,-1,-1"/>

                </ModelVisual3D.Content>

            </ModelVisual3D>

        </Viewport3D>

    </Grid>

</Window>
