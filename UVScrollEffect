using UnityEngine;
using UnityEngine.UI;

public class UVScrollEffect : BaseMeshEffect
{
    [SerializeField] private Vector2 scroll = new Vector2(1, 1);

    private Image _image;
    private Vector2 scrollDelta;

    protected override void Start()
    {
        _image = GetComponent<Image>();
    }

    public override void ModifyMesh(VertexHelper vh)
    {
        if (!IsActive()) return;
        if (!_image) return;

        int vertCount = vh.currentVertCount;

        scrollDelta = scroll * Time.time;

        UIVertex vert = new UIVertex();

        for (var i = 0; i < vertCount; i++)
        {
            vh.PopulateUIVertex(ref vert, i);
            vert.uv0 += scrollDelta;
            vh.SetUIVertex(vert, i);
        }
    }

    private void Update()
    {
        _image.SetVerticesDirty();
    }
}
