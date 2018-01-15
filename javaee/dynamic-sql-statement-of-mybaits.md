# Mybaits的动态SQL语句

```xml
  <update id="updateByExampleSelective" parameterType="map" >
    update tb_item
    <set >
      <if test="record.id != null" >
        id = #{record.id,jdbcType=BIGINT},
      </if>
      <if test="record.title != null" >
        title = #{record.title,jdbcType=VARCHAR},
      </if>
      <if test="record.sellPoint != null" >
        sell_point = #{record.sellPoint,jdbcType=VARCHAR},
      </if>
      <if test="record.price != null" >
        price = #{record.price,jdbcType=BIGINT},
      </if>
      <if test="record.num != null" >
        num = #{record.num,jdbcType=INTEGER},
      </if>
      <if test="record.barcode != null" >
        barcode = #{record.barcode,jdbcType=VARCHAR},
      </if>
      <if test="record.image != null" >
        image = #{record.image,jdbcType=VARCHAR},
      </if>
      <if test="record.cid != null" >
        cid = #{record.cid,jdbcType=BIGINT},
      </if>
      <if test="record.status != null" >
        status = #{record.status,jdbcType=TINYINT},
      </if>
      <if test="record.created != null" >
        created = #{record.created,jdbcType=TIMESTAMP},
      </if>
      <if test="record.updated != null" >
        updated = #{record.updated,jdbcType=TIMESTAMP},
      </if>
    </set>
    <if test="_parameter != null" >
      <include refid="Update_By_Example_Where_Clause" />
    </if>
  </update>
```



