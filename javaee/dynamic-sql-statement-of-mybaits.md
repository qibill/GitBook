# Mybaits的动态SQL语句

```xml
  <update id="updateByPrimaryKeySelective" parameterType="com.taotao.pojo.TbItem" >
    update tb_item
    <set >
      <if test="title != null" >
        title = #{title,jdbcType=VARCHAR},
      </if>
      <if test="sellPoint != null" >
        sell_point = #{sellPoint,jdbcType=VARCHAR},
      </if>
      <if test="price != null" >
        price = #{price,jdbcType=BIGINT},
      </if>
      <if test="num != null" >
        num = #{num,jdbcType=INTEGER},
      </if>
      <if test="barcode != null" >
        barcode = #{barcode,jdbcType=VARCHAR},
      </if>
      <if test="image != null" >
        image = #{image,jdbcType=VARCHAR},
      </if>
      <if test="cid != null" >
        cid = #{cid,jdbcType=BIGINT},
      </if>
      <if test="status != null" >
        status = #{status,jdbcType=TINYINT},
      </if>
      <if test="created != null" >
        created = #{created,jdbcType=TIMESTAMP},
      </if>
      <if test="updated != null" >
        updated = #{updated,jdbcType=TIMESTAMP},
      </if>
    </set>
    where id = #{id,jdbcType=BIGINT}
  </update>
```



